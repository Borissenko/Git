# Создание alias для консольных команд
//https://pingvinus.ru/note/alias


# Service - команды 
alias -p            //Посмотреть список всех ОДНО-КОМАНДНЫХ alias
unalias aliasName   //удаление
unalias -a          //удаление всех синонимов



# My alias

# git graph
gg ()
{
	git log --all --graph --decorate --oneline -M -C
}


# ==commit
gc ()
{
	git add -A && git commit -m "$1"
}



gca ()
{
	git add -A && git commit --amend --no-edit
}

# delete the last commit with keep changes
gcd ()
{
	git reset --soft HEAD~
}

# delete the last commit with NO keep changes
gcdd ()
{
	git reset --hard @~
}


# git go to branch
go ()
{
	git checkout "$1"
}



# git amend_commit & go to new branch
gcb ()
{
	git add -A && git commit --amend --no-edit && git checkout -b "$1"
}



# create and go to new branch
gob ()
{
	git checkout -b "$1"
}


# ==branch
# git branch 
bb()
{
	git branch
}

# показать все ветки, в т.ч. удаленные
bba()
{
	git branch -a
}


# git branch rename
br()
{
	git branch -m "$1"
}


# git branch delete
bd ()
{
	git branch -d "$1"
}


# git branch delete D
bdd ()
{
	git branch -D "$1"
}


# ==push
# git push
gp ()
{
	git push
}

# git push -f
gpp ()
{
	git push -f
}


# git go to branch & push upstream
gopp ()
{
	git checkout "$1" & git push --set-upstream origin "$1"
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
home/Nick/.bashrc
или
~/.bashrc

## снять ограничение на запись
sudo chmod -R -f 777 .bashrc

## в низу файла прописываем наш alias
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










