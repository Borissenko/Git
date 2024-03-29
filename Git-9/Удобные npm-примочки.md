# = Удобные примочки при работе с терминалом и  git'ом =


# NODE.js - nvm
## изменить дефолтную версию node in nvm
nvm alias default 16.15.1



# очистить кэш npm
npm cache clean -f



# параметры компьютера
sudo apt install htop  
htop                       \\ описание компа: ядра, память. Сколько памяти потребляется.
nproc                      \\сколько ядер у процессора компьютера
lscpu                      \\данные о компе развернуто
sudo dmidecode -t memory   \\параметры оперативной памяти


# fileCommander
sudo apt install mc
mc          \\ открыть fileCommander
ctrl + o    \\ закрыть fileCommander


pwd                    // копируем адрес файла
echo '' > error.log    // перетираем(стираем) содержимое в текущая_папка/error.log
echo '<?php phpinfo(); ?>' > /var/www/demo/info.php  //создали файл info.php и записали в него <?php phpinfo(); ?>

curl localhost  //Консоль как броузер: запускаем "броузер" по адресу localhost и распечатываем содержимое странички в консоле.


## какие процессы запущены
>ps -all -x


## какие пакеты установлены глобально
npm ls -g --depth=0
npm ls --depth=0        //глобально и локально


## создать файл package.json
>npm init
>npm init -y    //со значениями по-умолчанию


# переход в СУПЕРПОЛЬЗОВАТЕЛЯ, $ смениться на #
sudo bash      //пароль  90


# переход в ROOT-терминал. 
У root-пользователя по-умолчанию прописаны права суперпользователя.
sudo su -    // далее пароль  90    , (substitute user)
sudo -i      // далее пароль  90
sudo -s  //  В этом случае домашний каталог не сменится на /root, а останется пользовательский. Как правило, этот вариант удобнее.

После завершения задач, для которых требуются привилегии root, 
вернитесь в обычную оболочку с помощью следующей команды:
exit


# ПРАВА ДОСТУПА к файлу =
sudo chmod -R -f 777 ./folder  или fileName


## вернуть права обратно(!) to 755
sudo: /etc/sudoers.d is world writable 
- иногда так НЕ должно быль, файл открыт для записи.
поэтому команда sudo не будет срабатывать!
Надо его обратно вернуть в состояние 755(!).


## изменить файл ИЗ терминала
> сделай копию файла перед изменением его(!)

sudo su
echo "65" > /proc/sys/net/ipv4/ip_default_ttl

>> переписали ВСЕ содержимое файла на текст "65"


## изменить файл ИЗ текстового редактора vi или nano.
- тогда можно вносить изменения даже в защищенном файле тоже.

sudo su
sudo nano > /proc/sys/net/ipv4/ip_default_ttl

Ручками переписываем содержание файла -  65 в место 64
Сохраням и будет good!




# изменить TTL
sudo su
echo "65" > /proc/sys/net/ipv4/ip_default_ttl

Далее, ???
чтобы применить новую настройку, которую мы добавили, нам необходимо выполнить:
sudo sysctl -p

= ПРОВЕРКА =
ping 127.0.0.1

Ubuntu - 64
andpoid - тоже 64
Windows - 128

TTL имеет свойство уменьшаться на 1 при проходе через узел (в нашем случае это раздающее устройство),

поэтому нужно указать значение TTL=65 (на 1 больше, 65 вместо 64),
а если Windows — то указываем TTL=129 (вместо 128)




# Оставить npm-процесс работающим после закрытия терминала
>nmp run dev > /dev/null & kill -q process_pid



# остановить npm-процесс
sudo lsof -i tcp:3000            //какие процессы запущены
sudo kill -q process_pid          //process_pid - это номер процесса



# Запустить несколько скриптов одной npm-командой
npm i concurrently --save-dev

//server/package.json
"scripts": {
  "run": "concurrently 
    --names \"server, client\"
    \"nmp run server --silent\"
    \"nmp run client --silent\"
  ",
  "dev": "",
  "server": "nodemon server.js",
  "client": "cd client && npm run dev",          // здесь команда dev - прописана в client/package.json
  "installing": "npm i && cd client && npm i"    //одной командой инстиллируем пакеты в server/package.json и в client/package.json
}





# PHPStorm  
## Создаем файл
//Можно указывать и абсолютный, и относительный путь.
touch Desktop/fileHere.vue       

## ОТКРЫТЬ внешний ФАЙЛ В PHPStorm'e командой из консоли
phpstorm --line 3 ~/Desktop/fileHere.vue

## DIFF 2 файлов В PHPStorm'e командой из консоли
phpstorm diff ~/Desktop/fileHere.vue Home.vue 

phpstorm diff ~/Documents/URF_valid.vue  ~/Documents/URF_confirm.vue




## MERGE
phpstorm merge path1 path2 path3 output_file_path	
The path to the local copy of the file.
The path to the repository version of the file.	
(optional) The path to the base revision for path1 and path2.	
The path to the file to save the merge results in.





# Отменить ввод пароля при запуске Chrome.
sudo nano /usr/share/applications/google-chrome.desktop

заменить строчку (ТОЧНО именно такую строчку, т.к. есть еще ОЧЕНЬ похожие(!))
Exec=/usr/bin/google-chrome-stable  %U 
на 
Exec=/usr/bin/google-chrome-stable --password-store=basic %U

Теперь необходимо сохранить изменения в файл:
Сохранить    — Ctrl+O
               Enter
Закрыть файл — Ctrl+X






# Изменить ПАРОЛЬ, если не можешь войти в ноутбук
 Загрузиться на загрузочной флешке
 В терминале набрать
sudo fdisk -l     //какие диски на ноутбуке. Выбрать, на котором установлена твоя Linux, здесь - sda4.

Создадим директорию для монтирования нашего диска.
sudo mkdir /media/sda4

Следующая команда подмонтирует диск с папку  /media/sda1 folder.
sudo mount /dev/sda4 /media/sda4

Переходим в корневую директорю родной Ubuntu на ноутбуке:
sudo chroot /media/sda4

Теперь мы можем использовать команду passwd для изменения пароля пользователя.

Список пользователей (реальные пользователи - под конец списка):
cut -d: -f1 /etc/passwd

Меняем паспорт:
passwd <пользователь>

Перезагрузите систему с помощью команды reboot




# положение терминала
/usr/share/applications/gnome-terminal.desktop
Exec=gnome-terminal --geometry=100x50+800+300

100 - ширина экрана в символах
50 - высота в линиях
800 - x позиция окна
300 - y позиция окна




