@sqlmaster MIT License
[портабле версия клиента git под win и т.д. скачиваем здесь](https://git-scm.com/download/win)
```
создаем ярлык на консольную утилиту \git\git-cmd.exe
прописываем в него в Start in путь к репозиторию который мы уже получили командой clone
в Shortcut key: ярлыка биндим сочетание горячих клавиш, пример CTl+Alt+D
```
[наглядная справка](https://marklodato.github.io/visual-git-guide/index-ru.html)
# Работа с git  
- [Основы Git - Создание Git-репозитория](https://git-scm.com/book/ru/v2/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git-%D0%A1%D0%BE%D0%B7%D0%B4%D0%B0%D0%BD%D0%B8%D0%B5-Git-%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D1%8F)  
- [GitHub - Внесение собственного вклада в проекты](https://git-scm.com/book/ru/v2/GitHub-%D0%92%D0%BD%D0%B5%D1%81%D0%B5%D0%BD%D0%B8%D0%B5-%D1%81%D0%BE%D0%B1%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D0%BE%D0%B3%D0%BE-%D0%B2%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0-%D0%B2-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D1%8B)  
- [Как сделать свой первый Pull Request](https://rustycrate.ru/%D1%80%D1%83%D0%BA%D0%BE%D0%B2%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D0%B0/2016/03/07/contributing.html)  
 
## Псевдонимы в Git
```sh  
git config --global alias.co checkout  
git config --global alias.br branch  
git config --global alias.c commit  
git config --global alias.s status  
```
https://git-scm.com/book/ru/v2/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git-%D0%9F%D1%81%D0%B5%D0%B2%D0%B4%D0%BE%D0%BD%D0%B8%D0%BC%D1%8B-%D0%B2-Git#r_git_aliases  

## просмотреть все настройки  
```sh
git config --list --show-origin  
```
  
## Имя пользователя  
```sh
git config --global user.name "sqlmaster"
git config --global user.email globalalek@gmail.com  
```
## если проблемы с сертификатом
```sh
git config --global http.sslVerify false
```
настраиваем notepad вместо Vim  
https://stackoverflow.com/questions/13340329/how-to-save-a-git-commit-message-from-windows-cmd  

Расширение дерево для google chrome для работы с GIT   
Octotree - GitHub code tree  

Просмотр-истории-коммитов  
https://git-scm.com/book/ru/v2/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git-%D0%9F%D1%80%D0%BE%D1%81%D0%BC%D0%BE%D1%82%D1%80-%D0%B8%D1%81%D1%82%D0%BE%D1%80%D0%B8%D0%B8-%D0%BA%D0%BE%D0%BC%D0%BC%D0%B8%D1%82%D0%BE%D0%B2  
  
Origin - это наш репозиторий и main - это ремоут ветка. Если мы всегда так будет писать, то оно будет работать.   
Естественно каждый раз это писать лень, поэтому есть второй вариант.  
Второй вариант это указать трекинг информацию для этой ветки и тогда мы всегда будем пулить правильную ветку.  

git branch --set-upstream-to=origin/main  
https://monsterlessons.com/project/lessons/git-izuchaem-komandy-pull-i-push
  
## делаем pull автоматом на последние изменения в удаленном репозитории
```sh
git config --global --bool pull.rebase true
```
# Рекомендуется настроить Git на merges 
```sh
git config --local pull.rebase merges
git config --global pull.rebase merges  
```
## если both modified: .....
```sh
git mergetool
# применяем изменения в програме smerge
git s
del git_help.md.orig
git c -m "merge"
git rebase --continue
git pull
git push
```

## настраиваем merge утилиту  
```sh
git config --global merge.tool smerge  
git config --global mergetool.smerge.path "c:\Program Files\Sublime Merge\smerge.exe"
```
## Редактор
```sh
git config --global core.editor "vim"
git config --global core.editor "'c:\Program Files\Sublime Text\sublime_text.exe' -w"
```
## добавить URL удаленного репозитория  
```sh
git remote -v
git remote remove origin
git remote add origin git@github.com:PerynFr/miner.git
```
елси при `git pull`
fatal: отказ слияния несвязанных историй изменений
тогда
```sh
git pull --allow-unrelated-histories
git push
```
## изменить URL удаленного репозитория  
```sh
git remote -v   просмотреть текущий URL  
git remote set-url origin https://notabug.org/Peryn/temp.git  
```
Второй способ:  
Отредактировать файл .git/config: секция [remote "origin"] параметр - url.  

## дать права на дирректорию проекта git текущему пользователю если ошибка  
error: cannot open .git/FETCH_HEAD: Permission denied  
```sh
sudo chown -R $USER: .  
```  
## для исключения из индекса
```sh
git rm --cached log_file_info.txt   
```
##  Отменить локальные изменения
```sh
git reset --hard
```  
## Отмена изменений в файле  
```sh
git checkout -- CONTRIBUTING.md  
```
## Если необходимо вернуть файл до предыдущего состояни определенного коммита
необходимо в git log найти хэш ребуемого коммита и прописать 
```sh
git checkout commit_hash path_to_file
```
, где commit_hash - хэш необходимого коммита и path_to_file - путь до файла, который необходимо скинуть.
Пример: Я добавил в коммит и отправил в удаленную ветку ненужный файл. Поэтому командой git log нашел хэш предпоследнего коммита и выполнил команду: git checkout db449e5882a85636ae9444c24ec78fe135312ee3 widgets/assets/js/main.min.js
После чего снова запушил файл 
```sh
git add widgets/assets/js/main.min.js || git commit -m 'fix min.js' || git push origin CORE-2093. 
```
В репозитории в ПР файл откатился до начального состояния.
## Как отменить (откатить) действие git pull?  https://ru.stackoverflow.com/questions/361124/%D0%9A%D0%B0%D0%BA-%D0%BE%D1%82%D0%BC%D0%B5%D0%BD%D0%B8%D1%82%D1%8C-%D0%BE%D1%82%D0%BA%D0%B0%D1%82%D0%B8%D1%82%D1%8C-%D0%B4%D0%B5%D0%B9%D1%81%D1%82%D0%B2%D0%B8%D0%B5-git-pull
```sh
git reset --hard
git checkout sphere
git reflog
# Находите хэш коммита, в котором вы находились до первого pull-а.
# Будет что-то вроде "8f05e00 HEAD@{4}: checkout: moving from master to sphere"
# или "4c31200 HEAD@{10}: commit: Awesome feature implemented."
git reset --hard [нужный хэш]
```

## удаляем изменения из рабочей дирректории  
```sh
git restore db.db  
```
## Файл CONTRIBUTING.md изменен, но снова не индексирован. 
```sh 
git restore --staged CONTRIBUTING.md  
```  
## git rm, удаляет файл из вашего рабочего каталога  
## Если вы изменили файл и уже проиндексировали его, вы должны использовать принудительное удаление с помощью параметра -f  
```sh
git rm temp.md -f  
git rm "SQL decommissioning" -r  # удаляем католог рекурсивно  
```
# отслеживание изменений  
## если вы хотите увидеть сокращенную статистику для каждого коммита, вы можете использовать опцию --stat:  
```sh
git log --stat  
```
-p или --patch, который показывает разницу (выводит патч), внесенную в каждый коммит. Так же вы можете ограничить количество   
записей в выводе команды; используйте параметр -2 для вывода только двух записей  
```sh
git log -p -2  
```
-p  
Показывает патч для каждого коммита.  
--stat  
Показывает статистику измененных файлов для каждого коммита.  
--shortstat  
Отображает только строку с количеством изменений/вставок/удалений для команды --stat.  
--name-only  
Показывает список измененных файлов после информации о коммите.  
--name-status  
Показывает список файлов, которые добавлены/изменены/удалены.  
--abbrev-commit  
Показывает только несколько символов SHA-1 чек-суммы вместо всех 40.  
--relative-date  
Отображает дату в относительном формате (например, «2 weeks ago») вместо стандартного формата даты.  
--graph  
Отображает ASCII граф с ветвлениями и историей слияний.  
--pretty  
Показывает коммиты в альтернативном формате. Возможные варианты опций: oneline, short, full, fuller и format (с помощью последней   
можно указать свой формат).  
--oneline  
Сокращение для одновременного использования опций   
--pretty=oneline --abbrev-commit.  

## Problem with win1251 encoding  
I just added into file .git/config this lines:  
  
[gui]  
        encoding = cp1251  

# перемещение дирректории git mv a folder and sub folders in windows   
function Move-GitFolder {
    param (
        $target,
        $destination
    )
    
    Get-ChildItem $target -recurse |
    Where-Object { ! $_.PSIsContainer } |
    ForEach-Object { 
        $fullTargetFolder = [System.IO.Path]::GetFullPath((Join-Path (Get-Location) $target))
        $fullDestinationFolder = [System.IO.Path]::GetFullPath((Join-Path (Get-Location) $destination))
        $fileDestination = $_.Directory.FullName.Replace($fullTargetFolder.TrimEnd('\'), $fullDestinationFolder.TrimEnd('\'))

        New-Item -ItemType Directory -Force -Path $fileDestination | Out-Null

        $filePath = Join-Path $fileDestination $_.Name

        git mv $_.FullName $filePath
        
    }
}  

Применение  
  
Move-GitFolder <Target folder> <Destination folder>
  
Преимущество этого решения по сравнению с другими решениями заключается в том, что оно рекурсивно перемещает папки и файлы и даже   создает структуру папок, если она не существует.  
  
## способ 2  
## Убедитесь, что правильный путь выбран в консоли git при выполнении команды:  
```sh
git mv Source Destination  
```
При необходимости используйте:  
```sh
cd SourceFolder  
```
А затем команда mv.  

# Псевдонимы в Git   https://git-scm.com/book/ru/v2/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git-%D0%9F%D1%81%D0%B5%D0%B2%D0%B4%D0%BE%D0%BD%D0%B8%D0%BC%D1%8B-%D0%B2-Git#r_git_aliases  
```sh
git config --global alias.c commit  
git config --global alias.s status  
git config --global alias.l 'log -1 HEAD'  
```
## решаем проблему с merge
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   catalogs/price_dsv_mebel.xlsx
        modified:   db.db
        modified:   readme.txt
        modified:   run as systenctl.txt
        new file:   start.cmd

Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
        both modified:   .env


c:\Repository\PycharmProjects\vyrok_bot>git merge
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
error: Merging is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.

c:\Repository\PycharmProjects\vyrok_bot>git s
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
interactive rebase in progress; onto f11cc8b
Last command done (1 command done):
   pick b769b91 start.cmd
No commands remaining.
You are currently rebasing branch 'master' on 'f11cc8b'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   catalogs/price_dsv_mebel.xlsx
        modified:   db.db
        modified:   readme.txt
        modified:   run as systenctl.txt
        new file:   start.cmd

Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
        both modified:   .env

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.txt


c:\Repository\PycharmProjects\vyrok_bot>git add .
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"

c:\Repository\PycharmProjects\vyrok_bot>git mergetool
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
No files need merging

c:\Repository\PycharmProjects\vyrok_bot>git pull
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
error: cannot pull with rebase: Your index contains uncommitted changes.
error: please commit or stash them.

c:\Repository\PycharmProjects\vyrok_bot>git add .
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"

c:\Repository\PycharmProjects\vyrok_bot>git s
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
interactive rebase in progress; onto f11cc8b
Last command done (1 command done):
   pick b769b91 start.cmd
No commands remaining.
You are currently rebasing branch 'master' on 'f11cc8b'.
  (all conflicts fixed: run "git rebase --continue")

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   .env
        modified:   catalogs/price_dsv_mebel.xlsx
        modified:   db.db
        modified:   readme.txt
        modified:   run as systenctl.txt
        new file:   start.cmd


c:\Repository\PycharmProjects\vyrok_bot>git c -m "start.cmd"
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
[detached HEAD 69bafdf] start.cmd
 6 files changed, 78 insertions(+), 30 deletions(-)
 create mode 100644 start.cmd

c:\Repository\PycharmProjects\vyrok_bot>git push
fatal: You are not currently on a branch.
To push the history leading to the current (detached HEAD)
state now, use

    git push origin HEAD:<name-of-remote-branch>


c:\Repository\PycharmProjects\vyrok_bot>git pull
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
You are not currently on a branch.
Please specify which branch you want to rebase against.
See git-pull(1) for details.

    git pull <remote> <branch>


c:\Repository\PycharmProjects\vyrok_bot>git push --force
fatal: You are not currently on a branch.
To push the history leading to the current (detached HEAD)
state now, use

    git push origin HEAD:<name-of-remote-branch>


c:\Repository\PycharmProjects\vyrok_bot>git push origin HEAD:master --force
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 2 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (9/9), 121.50 KiB | 2.25 MiB/s, done.
Total 9 (delta 5), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (5/5), completed with 5 local objects.
To https://github.com/PerynFr/vyrok_bot.git
   f11cc8b..69bafdf  HEAD -> master

c:\Repository\PycharmProjects\vyrok_bot>git pull
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
You are not currently on a branch.
Please specify which branch you want to rebase against.
See git-pull(1) for details.

    git pull <remote> <branch>


c:\Repository\PycharmProjects\vyrok_bot>git s
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
interactive rebase in progress; onto f11cc8b
Last command done (1 command done):
   pick b769b91 start.cmd
No commands remaining.
You are currently editing a commit while rebasing branch 'master' on 'f11cc8b'.
  (use "git commit --amend" to amend the current commit)
  (use "git rebase --continue" once you are satisfied with your changes)

nothing to commit, working tree clean

c:\Repository\PycharmProjects\vyrok_bot>git rebase --continue
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
Successfully rebased and updated refs/heads/master.

# работа с ветками (ветки, ветка)
https://monsterlessons.com/project/lessons/git-uchimsya-rabotat-s-pravilnym-workflow  
## короткая форма записи, которая сразу создает ветку и переходит на нее  
```sh
git checkout -b develop 
git checkout develop # если ветка уже есть ее создавать ненадо
```
## мы создали develop ветку и перешли на него. Давайте запушим ее в репозиторий  
```sh
git push  
```  
## переходим на мастер и мерджим develop в мастер  
```sh
git checkout master  
git merge develop  
git push  
```
## удаляем локальную ветку -D Shortcut for --delete --force
```sh
git branch -d fix
```
https://webdevkin.ru/courses/git/git-merge  

# если не работает gitignore

## Чтобы отменить отслеживание одного файла, который уже был добавлен/инициализирован в ваш репозиторий, 
## т. е. остановить отслеживание файла, но не удалять его из вашей системы, используйте:  
```sh
git rm --cached filename  
```
## для всех файлов  
## Сначала зафиксируйте любые незавершенные изменения кода, а затем выполните эту команду:  
```sh
git rm -r --cached  
git add .  
git commit -m ".gitignore is now working"  
```

## Hастройка логина в GitHub через SSH Key на Linux   
```sh
alex@ubuntu:~/.ssh$ ssh-keygen -t ed25519 -f git_key -C "perynfr@github.com"
Generating public/private rsa key pair.


alex@ubuntu:~/.ssh$ cat git_key.pub
добавляем всю строку ниже в git settings/ssh and GPG keys/New SSH key

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCDHTF6m8BfRHvu6s+zsCJQeDdwHqbEDX7mXsKHtestsHOmauuJ2kskWF85eAq/Jbynh5IcXI/o6PlzPf4e6ytb7MjZ1hEeZ7Ron1/GvW9j9cghRIZ5sq7STfwmI4bVihW439u/biH6nUo0Io4F2x9gL3t4GQo1bkq9Y13kA2DG7Q2+Isf38bwSofWdBeHJWvstA/fGx0R24NqtdvJwVUyRl4N1KXuLgFZ2wg9i2W8m1mv94KwQ/FBgFQodd7qZKn1eU1UcvyObgjcpPVC/fws5kStVmTy7Rm+e0OENFn9n9M78aBf7qoi/NQeDD0axPL54M2PXsahWlBhwSZuGqJ+e7MH3BVZZ/OaGmsVsqa5pvylSkn500dk0ZdnRixB04MChqTYFphSEcHHe+vSDW8hkD9aPsCXBF7I6h38IItHRRLxEpD3W301wE/SuZAiP0= alex@ubuntu

далее 
git clone git@github.com:PerynFr/settings.git

если получаем ошибку:
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

то очищаем файл 
alex@ubuntu:~/.ssh$ cat known_hosts
и далее
alex@ubuntu:~/.ssh$ sudo chmod 600 git_key
alex@ubuntu:~/.ssh$ ssh-add git_key
если ошибка:
Could not open a connection to your authentication agent.
то запускаем агента
alex@ubuntu:~/.ssh$ eval `ssh-agent -s`

alex@ubuntu:~/.ssh$ ssh-add git_key
Identity added: git_key (alex@ubuntu)

alex@ubuntu:~$ git clone git@github.com:PerynFr/settings.git
Cloning into 'settings'...
успех

Чтобы сохранить настройки SSH и SSH-агента между сессиями, вам следует добавить необходимые команды в ваш файл запуска оболочки (например, `~/.bashrc` или `~/.zshrc`, в зависимости от используемой вами оболочки). Вот как это можно сделать:

1. **Откройте файл запуска оболочки:**
   ```bash
   nano ~/.bashrc
   ```
   или
   ```bash
   nano ~/.zshrc
   ```

2. **Добавьте следующие строки в конец файла:**
   ```bash
   # Start SSH agent
   eval "$(ssh-agent -s)"
   
   # Add your SSH key to the agent
   ssh-add ~/.ssh/ваш_ключ
   ```
   Замените `ваш_ключ` на имя вашего ключа.

3. **Сохраните изменения и закройте файл.**

4. **Перезапустите вашу оболочку или выполните:**
   ```bash
   source ~/.bashrc
   ```
   или
   ```bash
   source ~/.zshrc
   ```

Теперь при каждом запуске вашей оболочки эти команды будут автоматически выполняться, что позволит сохранить настройки SSH и SSH-агента между сессиями.

```
# пример для локального git
- [инструкция по git](https://github.com/PerynFr/MSSQL/blob/master/git_help.md)
- после установки git согласно инструкции, для создания локальной копии выполнить: 
```sh
git clone https://github.com/PerynFr/MSSQL.git
```
# Contributing

- чтобы внести свой вклад: команда ниже создает ветку и сразу переходит на нее,   
    вместо branch_name придумайте свое имя локальной ветки, после внесенных изменений запуште ее и создайте merge request с main
```sh    
git checkout -b branch_name
```
**Примечание**: *[черновая часть! для рассмотрения и обсуждения]*  
Пожалуйста, рассмотрите возможность добавления одного из следующих префиксов в заголовок вашего запроса на включение:  

- **feat**: новая функция  
- **fix**: исправление ошибки  
- **docs**: меняется только документация  
- **style**: форматирование, отсутствие точек с запятой, пробелы и т. д.  
- **refactor**: изменение кода, которое не исправляет ошибку и не добавляет новую функцию.  
- **perf**: изменение кода, повышающее производительность.  


