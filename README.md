# telegramBackup
How to backup your chats in telegram.
Thanks to https://www.haykranen.nl/2014/12/02/howto-backup-your-telegram-chats/

# Install telegram-cli
see https://github.com/vysheng/tg#installation

1. Clone GitHub Repository ```git clone --recursive https://github.com/vysheng/tg.git && cd tg```
2. Install libs: readline, openssl and (if you want to use config) libconfig, liblua, python and libjansson. If you do not want to use them pass options --disable-libconfig, --disable-liblua, --disable-python and --disable-json respectively.
```sudo apt-get install libreadline-dev libconfig-dev libssl-dev lua5.2 liblua5.2-dev libevent-dev libjansson-dev libpython-dev make```
3. Configure and make
``` 
./configure 
make
```

# Install telegram-history-dump
see https://github.com/tvdstaaij/telegram-history-dump

1. Clone GitHub Repository
```git clone --recursive https://github.com/tvdstaaij/telegram-history-dump.git && cd telegram-history-dump```
2. install ruby 
```sudo apt-get install ruby```
3. check version is >=2
```ruby --version```

# Run Telegram Cli and backup chats
see https://github.com/tvdstaaij/telegram-history-dump#performing-a-backup

1. Start telegram-cli
```./bin/telegram-cli --json -P 9009```
2. Insert your phone number the first time you start telegram-cli, e.g. +393401234567
3. Check ```config.yaml``` see https://github.com/tvdstaaij/telegram-history-dump#first-time-setup
4. Run backup ```ruby telegram-history-dump.rb```

# Transform from json to csv (optional)
not necessary if using html output, see https://github.com/tvdstaaij/telegram-history-dump#formatters

1. Download ```telegram-history-json-to-csv.py``` from https://gist.github.com/hay/7f5124f9992038d6c1ed00e1ed52772f
2. Install lib ```pip install unicodecsv```
3. Run the script ```python telegram-history-json-to-csv.py myBackupFolder/json/Name_Surname.jsonl Name_Surname.csv```

To run the script on ALL jsonl files:
```
for f in outputFolder/json/*.jsonl; do
  python telegram-history-json-to-csv.py  "$f" "${f%.jsonl}.csv"
done
```


# TODO
* check if new backups are incremental
