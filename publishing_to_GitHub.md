cd ~/repository/c/seed
git add seed.c BIP39.txt README.md .gitignore
git commit -m "Add project files"
git remote add origin git@github.com:psqlmaster/seed.git
git pull origin master --allow-unrelated-histories
git add <conflicted_file>
git commit -m "Resolve merge conflicts"
git push -u origin master
git push --force origin master
