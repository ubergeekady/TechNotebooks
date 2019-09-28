```
git config --global user.name "Aditya Singh"
git config --global user.name "adysingh1989@gmail.com"
git config --list
ls -la

git reset (untrack from staging area)
git reset <filename>
git add <filename>
git add . (track files, add them to staging area)

git commit -m "Message"

MacBooks-MacBook-Pro:creditrisk macbookpro$ git remote -v
origin	https://github.com/ollycredit/creditrisk.git (fetch)
origin	https://github.com/ollycredit/creditrisk.git (push)

MacBooks-MacBook-Pro:creditrisk macbookpro$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/ParamFeature
  remotes/origin/arpit_20Sep19
  remotes/origin/master
```

```
git branch -a (List all branches along with the current branch which is active)
git branch <branchname> (create new branch)
git checkout <branchname> (switch to this branch)

Make changes

git add .
git commit -m "Changes"
```

Merging on command line and pushing (check again)

```
git checkout master
git pull origin master
git branch --merged
git merge <branchname>
git push origin master
```

Deleting a branch

```
git branch -d Aditya_01
git push origin --delete Aditya_01
```

