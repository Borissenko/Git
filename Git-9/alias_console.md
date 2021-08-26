# Создание alias для консольных команд
//https://pingvinus.ru/note/alias


# Service - команды 
alias -p            //Посмотреть список всех ОДНО-КОМАНДНЫХ alias
unalias aliasName   //удаление
unalias -a          //удаление всех синонимов



# My alias
gc ()
{
	git add -A && git commit -m "$1"
}



gca ()
{
	git add -A && git commit --amend --no-edit
}

# git graph
gg ()
{
	git log --all --graph --decorate --oneline -M -C
}


# git gco
gco ()
{
	git checkout "$1"
}


# git amend_commit & go to new branch
gcb ()
{
	git add -A && git commit --amend --no-edit && git checkout -b "$1"
}


# git new branch
gb ()
{
	git checkout -b "$1"
}


# git branch delete
gbd ()
{
	git branch -D "$1"
}


# 
status777 ()
{
	sudo chmod -R -f 777 "$1"
}


//"$1" - это fileName
//формат декларации - именно такой(!)
// использование
status777 fileName




# Где декларируем
nano ~/.bashrc

в низу файла прописываем наш alias
Сохраняем изменения и закрываем файл. Для этого нажмите 
>Ctrl+X               // откроется запрос на сохранение изменений в файле. Жмем:
>y
>Enter.

ЗАНОВО открыть терминал.





# декларируем одно-командные alias
alias c="clear"




# декларируем много-командные синонимы и синонимы с аргументами
mkcd() {
  mkdir -p -- "$1" && cd -P -- "$1"
}

или

mkcd() {
  mkdir -p -- "$1" 
  cd -P -- "$1"
}

--        - используется, чтобы указать, конец опций команды
$1, $2    - чтобы внутри функции обратиться к аргументам




# использование
mkcd mynewdir










