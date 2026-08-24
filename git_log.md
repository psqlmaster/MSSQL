git log --oneline --graph --all

git log --oneline --graph --all --name-only
```
* 63f7a72 feat(gfm): Enhance gfm_control and gfm_switchover with multi-instance support, dynamic
| plugins/gfm/gfm_control.sh
| plugins/gfm/gfm_switchover.sh
```

git log --oneline --graph --all --stat
```
* 63f7a72 feat(gfm): Enhance gfm_control and gfm_switchover with multi-instance support, dynamic
|  plugins/gfm/gfm_control.sh    | 88 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++---------------
|  plugins/gfm/gfm_switchover.sh | 40 ++++++++++++++++++++--------------------
|  2 files changed, 93 insertions(+), 35 deletions(-)
```

### копироввать измененные файлы в другой проект
git diff-tree --no-commit-id --name-only -r HEAD
```
plugins/gfm/gfm_switchover.sh
```

git diff-tree --no-commit-id --name-only -r HEAD | xargs -I {} cp --parents {} /home/su/repository/c/gorgona_github/

git diff-tree --no-commit-id --name-only -r 060896f | xargs -I {} cp --parents {} /home/su/repository/c/gorgona_github/


