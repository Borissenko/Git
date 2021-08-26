# git_alias

# декларация в .profile
alias gs='git status '
alias ga='git add '
alias gb='git branch '
alias gc='git commit'



# декларация в .gitconfig проекта(?)

[alias]
  co = checkout
  ci = commit
  st = status
  

# Мои ALIASES
## посмотреть перечень уже заявленных
git config --list


## декларация ГЛОБАЛЬНO
git config --global alias.st status
git config --global alias.gr "log --all --graph --decorate --oneline -M -C"
git config --global alias.graph "log --all --graph --decorate --oneline -M -C"

git config --global alias.ci commit
git config --global alias.ca "commit --amend --no-edit"


git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.bra "branch -a"

git config --global alias.mff "merge --no-ff"
git config --global alias.ca "commit --amend --no-edit"    //amend-commit + без изменения комментария


git config --global alias.di diff
git config --global color.ui true
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.tags "tag -n" 




## alias для 2 команд (add+commit)  //no work
git config --global alias.сa '!git add -A && git commit --amend --no-edit'
git config --global alias.сс '!git add -A && git commit -m $1'                   //использование git cc привет   ,  $1 - это аргумент "привет".


## использование
git st









