# увидеть изменения в ветке
git diff dev

# скопировать изменения в head в другой репо
git diff-tree --no-commit-id --name-only -r HEAD
git diff-tree --no-commit-id --name-only -r HEAD | xargs -I {} cp --parents {} /home/su/repository/c/gorgona/

# скопировать изменения в от комита до head в другой репо
git diff --name-only -r 1545044..HEAD | xargs -I {} cp --parents {} /home/su/repository/c/gorgona_github/

# посмотреть какие файлы отличаются
diff -qr \
--exclude=.git \
--exclude=.cache \
/home/su/repository/c/gorgona/common \
/home/su/repository/c/gorgona_github/common
