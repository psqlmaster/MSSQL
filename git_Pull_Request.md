# Команды для работы с PR

## 1. Получить PR локально

```bash
git fetch origin pull/12/head:pr-branch          # Скачать PR #10 в ветку pr-branch
git checkout pr-branch                           # Переключиться на ветку
```

## 2. Проверить изменения

```bash
git diff master                                  # Посмотреть все изменения
git diff --name-only master                      # Только имена файлов
git log --oneline master..pr-branch              # Список коммитов в PR
```

## 3. Обновить мастер

```bash
git checkout master                              # Переключиться на мастер
git pull origin master                           # Обновить мастер
```

## 4. Смержить в мастер

```bash
git checkout master                              # Быть на мастере
git merge pr-branch                              # Обычный merge
```

Или с squash:

```bash
git merge --squash pr-branch                     # Склеить все коммиты в один
git commit -m "Merge PR #10: описание"           # Создать коммит
```

## 5. Разрешить конфликты (если есть)

```bash
git status                                       # Посмотреть конфликтные файлы
# Отредактировать файлы вручную
git add .                                        # Добавить исправления
git commit -m "Merge PR #10 with conflicts"      # Завершить merge
git merge --abort                                # Отменить merge если нужно
```

## 6. Запушить в репозиторий

```bash
git push origin master                           # Запушить мастер
```

## 7. Удалить ветку PR

```bash
git branch -d pr-branch                          # Удалить локальную ветку
git branch -D pr-branch                          # Принудительно удалить
```

## Полный цикл одной командой

```bash
git fetch origin pull/10/head:pr-branch && git checkout master && git pull origin master && git merge pr-branch && git push origin master && git branch -d pr-branch
```
