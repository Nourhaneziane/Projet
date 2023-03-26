# Projet
#!/bin/bash

url='https://www.marketwatch.com/investing/cryptocurrency/btcusd'

res=$(curl $url | grep "/zigman2/quotes/31322028/realtime>*" | head -2 |tail -1 | cut -d'>' -f 2 | cut -d'<' -f 1 | tr ',' '.')
current_date_time=`date '+%d-%B-%Y %T'`

echo "$res $current_date_time"> test.txt
sed 's/ \+/,/g' test.txt >>test.csv

