# Просмотр проекта, в т.ч. через мобильный телефон, временно задиплоив его.
//ngrok.com/docs


# How to install ngrok on Ubuntu:
sudo apt update
sudo snap install ngrok


# Далее запускаем проект локально via "npm run serve",
смотрим, на каком порту проект открылся,
и обозначаем этот же порт в запрос ngrok'а:

> ngrok http 3000      //запускаем ngrok, который будет слушать порт 3000

или
ngrok http http://localhost:8080
или, 
если вместо сайта появляется "Invalid Host Header", то запускаем via
ngrok http 8080 -host-header="localhost:8080"              <<best

или
ngrok http --host-header=rewrite 8080


=>>в консоле напишется www-адрес, по которому мы можем смотреть наш проект.


# ОПЦИИ для "ngrok http":
--auth       включает basic аутентификацию на конечной точке туннеля, 'ПОЛЬЗОВАТЕЛЬ:ПАРОЛЬ'
--authtoken      токен ngrok.com для аутентификации пользователя
--bind-tls "both"    прослушивать http, https или both: true/false/both
--config     путь до конфигурационных файлов; если указано несколько, то они используются все
--host-header    установить заголовок Host; если 'rewrite' использовать локальный адрес в качестве имени хоста
--hostname       туннель хоста на произвольном имени (требует DNS CNAME)
--inspect        включить/отключить интроспекцию (самоанализ) http
--log "false"    путь до файла журнала, 'stdout', 'stderr' или 'false'
--log-format "term"  формат записи журнала: 'term', 'logfmt', 'json'
--log-level "info"   уровень журнала
--region         регион сервера ngrok [us, eu, au, ap, sa, jp, in] (по умолчанию: us)
--subdomain      разместить туннель на указанном субдомене



.......................
см. команды также здесь
https://kali.tools/?p=5489
