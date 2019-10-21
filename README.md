# guide-to-testnet-v0.1.0
EVEN testnet guide

[English Guide](https://github.com/evenfound/guide-to-testnet-v0.1.0#english-guide)

[Инструкция на русском](https://github.com/evenfound/guide-to-testnet-v0.1.0#инструкция-на-русском)
## English Guide
## Инструкция на русском
### Установка 

Разархивировать файлы .zip

Создать папку ~/even-data (В windows C:/Users/<uname>/even-data)

В переменную среду ос добавить в PATH  полный путь к  even-data

Переносить even, evenctl, ipfs в директорию even-data

После установки IPFS (но не открывая IPFS) нужно инициализировать конфигурации 

$ even init --verbose

после выполнения этой команды в директории $HOME/.config/even появляются конфигурационные файлы 

Для запуска нода нужны выполнять команду 

even start --testnet [--verbose]


### Работа с пирами 

Получить свой идентификатор 

$ evenctl peer id
QmRGzxoGii5jQDwQRdiEsiiRhHdZL7DJ6Fscy2ZUA95m5S

Получить список пиров в сети 

$ evenctl peer list
QmRGzxoGii5jQDwQRdiEsiiRhHdZL7DJ6Fscy2ZUA95m5S
QmRGzxoGii5jQDwQRdiEsiiRhHdZL7DJ6Fscy2ZUA95m5S
QmRGzxoGii5jQDwQRdiEsiiRhHdZL7DJ6Fscy2ZUA95m5S
QmRGzxoGii5jQDwQRdiEsiiRhHdZL7DJ6Fscy2ZUA95m5S



### Создание кошелька 

evenctl wallet create
Enter the private passphrase for your new wallet: 
Please confirm the phrase you just entered: 
Do you have an existing mnemonic phrase you want to use? (n/no/y/yes) [no]: n
Do you have an existing wallet seed phrase you want to use? (n/no/y/yes) [no]: n
Your wallet generation mnemonic phrase is
******************************************************************************************
special immense gentle trend trend language glass result wink toddler grain wise

.......................................................................................

При выполнении этой команды нужно указать пароль и мнемоническая фраза 

После выполнение этой команды можно сразу перейти на генерацию аккаунта . Но для етого нужно сперва разблокировать 
аккаунт с паролем который указали при создании кошелька  

$ evenctl wallet unlock
Provide existing wallet private passphrase: 
2019/10/11 13:56:25 Call completed [Network: testnet]: map[even:unlocked]

$ evenctl wallet nextaccount
2019/10/11 13:56:29 Call completed [Network: testnet]: map[even:address:"mm65wXwTEKyc2vGksSuTTzJBu54AuS2yN7" ]

После генерации аккаунтов можно получить баланс 
$ evenctl wallet balance -l mm65wXwTEKyc2vGksSuTTzJBu54AuS2yN7

2019/10/11 14:07:45 Call failed [Network: ]: wallet has no funds

и отправить платежную транзакцию 

$ evenctl wallet tx pay  -t mm65wXwTEKyc2vGksSuTTzJBu54AuS2yN7 -f mm65wXwTEKyc2vGksSuTTzJBu54AuS2yN7 -v 1000


### Работа с папками 

Получение всех файлов в папке  shared / ledger

$ evenctl folder list shared
2019/10/11 14:11:34 shared:
/home/yuri/.config/even/shared/GENESIS_a5214607c0b7f7866797691371de2e40133e8c56f5a2500ba877b9be4fe22f5d_1559652360000000000

Добавление файла в директорию 

$ evenctl folder write shared  -f /bin/bash
2019/10/11 14:14:17 QmYtMhLMFzHV6VhkxjBwQqGMWwF8vcgUb7GuNRaYB91yLf
