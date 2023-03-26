# Генерация SSH-ключей

#1. создать папку /home/<ваш_пользователь>/.ssh/, 
если ее еще нет,
перейти в нее
>cd ~/.ssh
> (/c/Users/borisenko/.ssh/id_rsa) for Windows_10

#2. Генерируем ключевую пару 
ssh-keygen -t ed25519 -C "myKeyName"
или
ssh-keygen -t rsa -b 4096 -C "myKeyName"

#3. Регистрируем ПРИВАТНЫЙ ключ на ЛОКАЛЬНОМ ноутбуке
- что бы не вводить пароль к ключу каждый раз при использовании.
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/myKeyName          //=>>Identity added: /home/user/.ssh/github_key-5 (github_key-5)

#4. Добавляем к ключу fingerprint? НЕ ДЕЛАЛ.
ssh-add -l -E sha256          ?  //Find and take a note of your public key fingerprint.

#5. Проверяем, какие ключи на ноутбуке зарегистрированы
ls -al ~/.ssh                  //какие ключи установлены

#6. Копируем в буфер обмена код ПУБЛИЧНОГО ключа
cat ~/.ssh/id_rsa.pub   //перейти в папку ~/.ssh/ и скопировать публичный ключ одной командой

#7. Вставляем код приватного ключа в окошечко на GitHub
#8. Проверяем, что связка ключей работает.
ssh -T git@github.com
ssh -T git@bitbucket.org

#9. Если у вас уже есть хранилище, которое вы клонировали по HTTPS, 
измените URL-адрес вашего хранилища в .git/config, по стандарту его SSH_URL.

