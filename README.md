# UsedC_infra
UsedC Infra repository

Добавлен inventory ansible, а также сделан плейбук для затягивания репозитория.

Добавлены шаблонизированные конфиги terraform. Также они были разбиты на версии для stage и prod.

Добавлен файл-шаблон для packer. Был создан образ по шаблону, а также ВМ по этому образу.

Для подключения к someinternalhost в одну команду можно воспользоваться пробросом портов:
ssh -i ~/.ssh/appuser -f -N -A -L [порт локалхоста]:[внутренний IP someinternalhost]:22 appuser@[Внешний IP BastionHost]

После чего для подключения к внутреннему серверу можно воспользоваться:
ssh -i ~/.ssh/appuser -A appuser@localhost -p [порт локалхоста, на котором установили проброс]

Для подключения по алиасу можно настроить конфиг ssh в ~/.ssh/config:
Host someinternalhost
    HostName localhost
    User appuser
    Port [порт для проброса]
    IdentityFile ~/.ssh/appuser
    ForwardAgent yes

bastion_IP = 130.193.38.79
someinternalhost_IP = 10.130.0.26

testapp_IP = 178.154.228.76
testapp_port = 9292
