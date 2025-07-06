git reflog
git log --oneline --graph --all

# смотрим все ли там
git checkout 5ea1e78
## можно создать новую ветку
git checkout -b новая-ветка 5ea1e78

## если все там возвращам мастер
git checkout master
git reset --hard 5ea1e78
git push --force origin master

## проверяем 
git branch
git log --oneline

## очистить репо
git gc --prune=now

## Перебазируйте историю, чтобы удалить ненужные коммиты:
git rebase --onto 6c9f3c4 521486b master

git log --oneline --graph --all
