###COmmands

- beautiful logs
```
git log --graph --all --decorate
```

- show all the commits
```
git reflog
```

- reset to particular commit, cleans up the working dir (clears the staged file). Resets the index and working tree. Any changes to tracked files in the working tree since <commit> are discarded.
```
git reset --hard  [commit_hash or tag]
```
- Remove untracked files from the working tree. Cleans the working tree by recursively removing files that are not under version control, starting from the current directory.
```
git clean
```
- create a branch
```
git branch [new branch name]
```
- go to a branch
```
git checkout [branch]
```
- start local got server
```
git instaweb
```
- get content from remote
```
git fetch [remote-name]
```
- get content from remote and merge
```
git pull [remote-name]
```
- show all remotes
```
git remote -v
```
- add a remote
```
git remote add [name] [url]
```
- add tag
```
git tag [tag] -a -m "[my tagging message]"
```
- add a tag and gpg sign
```
git tag -s [tag] -m "[my tagging and signing message]"
 ```
- verify gpg sign tag
```
git tag -v [tag]
```

- show all the commits with signatures
```
git log --show-signature
```

- get all the tags from remote with content
```
git fetch origin --tags
```

- push all the tags to remote with content
```
git push origin master --tags
```

- list all the files in a repo
```
git --ls-files --stage
```
- Add interactively. Allows you to commit part changes in same file [using patches]. Lets say you made two changes in a file but want to. Stage only one change. You can use this command.
```
git add -i
```

- Who changed what
```
git blame [file]
```
- store the work you have been doing, so you can work on something else
```
git stash
```
- show all the stashes
```
git stash list
```




### GIT Config alias

- single line beautiful log
```
	lg=log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
	lol = log --graph --decorate --pretty=oneline --abbrev-commit
	lola = log --graph --decorate --pretty=oneline --abbrev-commit --all
```
-  will put a file into gitignore
```
 	ignore=!([ ! -e .gitignore ] && touch .gitignore) | echo $1 >>.gitignore
```
-  list aliases
```
	alias = !git config --list | grep 'alias\\.' | sed 's/alias\\.\\([^=]*\\)=\\(.*\\)/\\1\\t=> \\2/' | sort
```
-  take named stash
```
	snapshot = !git stash save "snapshot: $(date)" && git stash apply "stash@{0}"
```


### Notes
- HEAD where your current pointer is, and thats where all the action takes place.
