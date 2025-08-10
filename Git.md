# Проверить, установлен ли гит. Узнать его версию
git --version

# Склонировать репозиторий через протокол https
git clone https://<git_server>:<user_name>/<repository_name>.git

# Склонировать репозиторий через протокол ssh
git clone git@github.com:<user_name>/<repository_name>.git

# Добавить все файлы в индекс гита
git add .
# Добавить конкретный файл в индекс гита
git add <file_name>

# Удалить все файлы из индекса гита
git restore --staged
# Удалить конкретный файл из индекса гита
git restore --staged <file_name>

# Сделать коммит в локальную ветку и отправить изменения в удалённую ветку
git commit -m "Add new feature"
git push origin <branch_name>

# Создать удалённую ветку и переключить её на новую удалённую ветку
git checkout <branch_name>
git pull origin <branch_name>

# Удалить локальную ветку
git branch -d <branch_name>

# Удалить удалённую (remote) ветку
git push origin --delete <branch_name>

# Узнать текущую локальную ветку в гите
git branch --show-current

# Узнать текущую удалённую (remote) ветку в гите
git remote show origin

# Слить в текущую ветку изменения из указанной ветки
git merge <branch_name>

# Слить в текущую ветку изменения из указанной ветки с объединением коммитов
git merge --squash <branch_name>

# Объединение коммитов в один с изменением истории коммитов в ветке
# Тут нужно заменить pick на squash для объединяемых последних коммитов. 
# Список читается снизу вверх, таким образом последний коммит, это самый нижний коммит в списке.
# Сохранить файлы в открывшихся текстовых редакторах
git rebase --root -i