![hF4a1-NCaYapF4MfsOims](https://github.com/Mozgiii9/AvailSetupTheNode/assets/74683169/e5a2243e-b754-4401-bb8a-6dfc47879233)

# Avail. Разбор проекта + установка Light ноды + выполнение квестов. Погнали!

**Avail** — это децентрализованный уровень доступности данных, предназначенный для поддержки блокчейн-приложений нового поколения и суверенных Rollups.

**Инвестировали: $27 000 000.**

**Инвесторы: Founders Fund, DragonFly Capital, Balaji Srinivasan и другие.**

**Характеристики сервера:** 
- *4CPU/8RAM/300SSD/Ubuntu 22.04 — рекомендованные*
- *2CPU/4RAM/40SSD/Ubuntu 22.04 — минимальные*

**Ссылки:**
- [Web-site](https://www.availproject.org/)
- [Discord](https://discord.com/invite/y6fHnxZQX8)
- [Twitter](https://twitter.com/AvailProject)

Недавно анонсировали [челлендж **Avail’s Light Client Lift-Off**](https://lightclient.availproject.org/). Теперь официально просто принять участие и получить шанс выиграть награды сообщества и сминтить первую NFT за выполненные задания.

### ДЕДЛАЙН КВЕСТА: 9 АПРЕЛЯ! Не затягивайте, вполне возможно, что данная NFT - один из мультипликаторов дропа Avail.

![image](https://github.com/Mozgiii9/AvailSetupTheNode/assets/74683169/a74887ed-b0f0-496a-ac08-08f9b4489033)

### Что нам понадобится?:

- Сервер нужной конфигурации;
- Установленный кошелек SubWallet или любой другой кошелек, связанный с Polkadot. Линк на скачивание SubWallet - [ТЫК](https://www.subwallet.app/download.html);
- Discord, Telegram, Twitter - типичный набор криптана;
- Терпение, потому что [кран](https://faucet.avail.tools/) лагает ужасно.

**Начнем с установки ноды.**

**1. Обновляем содержимое сервера:**

```
sudo apt update && sudo apt upgrade -y
```

**2. Устанавливаем screen:**

```
sudo apt install screen
```

**3. Устанавливаем ноду одной командой:**

```
curl -sL1 avail.sh | bash
```

Появится логи, рано или поздно появится ошибка что нода отваливалась. Создадим скрипт для автоматического рестарта ноды:

**4. Выполним команды по очереди:**

```
rm -rf /root/.avail/data
```

```
screen -S node
```

```
sudo nano availscript.sh
```

Откроется пустой файл. Вставляем туда код, заменять ничего не нужно:

```
#!/bin/bash
# official script command of Avail script from daningyn
COMMAND="curl -sL1 avail.sh | bash"
# Here is script making LC restart if getting errors
while true; do echo "Starting command: $COMMAND"
    # Run command in the background
    bash -c "$COMMAND" &

    PID=$!

    wait $PID; EXIT_STATUS=$?
    if [ $EXIT_STATUS -eq 0 ]; then 
        echo "Command exited successfully. Restarting..."
    else 
        echo "Command failed with status $EXIT_STATUS. Restarting..."
    fi

    sleep 10
done
```

![image](https://github.com/Mozgiii9/AvailSetupTheNode/assets/74683169/e027441b-f15b-46a9-a846-686351e0d701)

*Что делает скрипт? Нода Avail достаточно проблемная, а учитывая, что все побежали сейчас абузить эту NFT - она стала падать еще чаще. Скрипт следит за состоянием ноды и в случае возникновения ошибки перезагружает ее.*

**Как вставили, прожимаем на клавиатуре CTRL + X — Далее жмём Y — Enter**

**Далее прожмите на клавиатуре кнопки CTRL + A + D (выходим из данной сессии screen). Очистится терминал и мы можем двигаться к следующему этапу.**

**5. Далее выполняем команду и заходим в блокнот и копируем нашу Seed Phrase, после чего сохраняем ее в надежное место:**

```
nano .avail/identity/identity.toml
```

![image](https://github.com/Mozgiii9/AvailSetupTheNode/assets/74683169/5a7c961d-c9e9-4fc0-84fc-7f7616caa11c)

**ВАЖНО! Внимательно копируйте Seed Phrase!**

**6. Как скопировали, прожимаем на клавиатуре CTRL + X. После чего запускаем ноду серией команд(вводим по очереди):**

```
rm -rf /root/.avail/data/LOCK
```

```
bash availscript.sh
```

**Отсюда копируем публичный ключ (Public Key) и так же сохраняем.**

![image](https://github.com/Mozgiii9/AvailSetupTheNode/assets/74683169/ca2cfede-6e8f-4315-993b-e81a08ad614d)

### Готово! Больше мы ничего не трогаем и не проверяем, если нода будет падать, то скрипт, который мы установили, будет автоматически её запускать заново. А мы пока перейдем к выполнению квеста, связанного с получением заветной NFT.

![image](https://github.com/Mozgiii9/AvailSetupTheNode/assets/74683169/7faacbdc-a9ab-4809-a4e4-7be8a21f40a2)

### Гайд по прохождению квестов:

**1. Устанавливаем [SubWallet](https://www.subwallet.app/download.html) и вставляем нашу Seed Phrase из ноды (см. этап 5);**

**2. В кошельке SubWallet нажимаем на кнопку "Get Address" и вписываем "Avail" — далее копируем адрес;**

**3. Переходим в [кран](https://faucet.avail.tools/);**

**4. Вставляем адрес Avail, который мы копировали в SubWallet, запрашиваем токены;**

**5. Переходим к выполнению квестов;**

**6. В четвёртом задании нужно вставить публичный ключ(Public Key, см. этап 6);**

**7. После выполнения всех заданий смело минтим NFT, нажав на кнопку "Mint Participation NFT".**

## FAQ:

**1. Деражть ноду актуально лишь на время данного квеста(до 9 апреля)? Далее можно не держать?**
- **Вы можете держать ноду по своему усмотрению, но я бы рекомендовал не сворачивать ее. Проект имеет достойный инвест + токен подтвержден и выдйет в первой половине 2024, а значит в самое ближайшее время**

**2. У меня возникла ошибка по ходу прохождения квестов. Что мне делать?**
- **По ходу прохождения квестов у меня не работали некоторые задания и я в итоге получил 350 очков вместо 450, но я все равно смог заминтить NFT. Не обязательно выполнять все задания, смотрите на доступность кнопки минта NFT. Важно понимать, что транзакция с минтом также может пройти не сразу, т.к. сеть перегружена.**

## Обязательно проведите собственный ресерч проектов перед тем как ставить ноду. Сообщество NodeRunner не несет ответственность за Ваши действия и средства. Помните, проводя свой ресёрч, Вы учитесь и развиваетесь.

Связь со мной: [Telegram(@M0zgiii)](https://t.me/m0zgiii)

Мои соц. сети: [Twitter](https://twitter.com/m0zgiii) 


