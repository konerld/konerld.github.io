# Telegram bot

## Installing
    apt-get update && apt-get upgrade
    apt-get install python3

    sudo python3 get-pip.py
    sudo pip install telepot
    sudo apt-get install python3-psutil
    apt-get install python3-matplotlib -y
    sudo apt-get install git
    git clone https://github.com/geekbeard/ServerStatsBot.git
    cd ServerStatsBot

    pip install pyTelegramBotAPI




BASH

#!/bin/bash

TOKEN=<ТОКЕН>
CHAT_ID=<ID_ЧАТА>
MESSAGE="Hello World"
URL="https://api.telegram.org/bot$TOKEN/sendMessage"
curl -s -X POST $URL -d chat_id=$CHAT_ID -d text="$MESSAGE"



Q > Как отправить сообщение curl'ом
A > example:
    curl -s -X POST https://api.telegram.org/bot<TOKEN>/sendMessage -d chat_id=<CHAT_id> -d text="Hello World"
