# Kaspersky Endpoint Security
## Установка с помощью Ansible для RPM-based дистрибутивов

### Настройка

В файле `hosts` можно оперировать версиями KES и KA, а так же их наличием для различых хостов задавая переменные `KES_PRESENT`, `KES_VERSION`, `KA_VERSION`

В переменных `KES_RPM` и `KA_RPM` в файле `./roles/kaspersky/vars/main.yml` необходимо задать задать шаблон url с предварительно размещенными Kaspersky Endpoint Security и Kaspersky Linux Network Agent rpm пакетами, формат именования пакетов стандартный для пакетов Kaspersky:  
* `kesl-{{ KES_VERSION }}.x86_64.rpm`  
* `klnagent64-{{ KA_VERSION }}.x86_64.rpm'`

Так же, необходимо задать адрес сервера администрирования в переменной `KLNAGENT_SERVER` в файле `./roles/kaspersky/vars/klnagent.yml`  

Остальные пременные настраиваются индивидуально, в случае необходимости.

### Использование

`ansible-playbook kaspersky.yml -i hosts.yml -e "TARGET=all"`