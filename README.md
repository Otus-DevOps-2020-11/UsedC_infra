# UsedC_infra
UsedC Infra repository

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
