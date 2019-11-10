# How to use git

## Local git repository

	```
	git init <repo_name>
	git add <target_file>
	git commit -m "commit message"
	git clone <repo_name> <target_directory>
	git status
	git diff
	git log
	git reflog
	git reset --hard <reflog_id>

	git checkout -- <file> // go back to latest add or commit
	git reset HEAD <file> // go back to lastest commit
	```

## Branch

	```
	git checkout -b dev
	git add & git commit
	git checkout master
	git merge dev
	git branch -d dev // delete dev
	git branch -D dev // delete dev whether merged
	```

### branch strategy

keep master stable, only use to release new version.

use dev to develop volatile features.

### issue branch

	```
	git stash // cache half-done folder
	git checkout master
	git checkout -b issue-101
	git add & git commit
	git checkout master
	git merge -m "merged issue-101" issue-101
	git checkout dev
	git stash list
	git stash apply stash@0 // continue with half-done folder
	git stash drop // drop stash
	git stash pop // continue and drop stash
	```
  
## Remote git repository

	```
	git remote add <remote_repo_name> <git@github.com:Logan-Shi/multi-robot-mapping.git> 
	git remote -v
	git push <remote_repo_name> <remote_branch>
		<-u> to connect remote with local, used for the first push
		<-f> to force push to remote repo, don't use, can cause extra trouble
	git pull <remote_repo_name> <branch>:<remote_branch>
	```

### cooperation

	```
	git clone git@github.com:Logan-Shi/multi-robot-mapping.git
	git checkout -b dev origin/dev **VERY IMPORTANT, MUST REMEMBER**
	git add & git commit
	git push origin dev
	```

solve conflict
	
	```
	git branch --set-upstream-to=origin/dev dev
	git commit -m "fix conflict"
	git push oringin dev
	```

## Other features

### git ignore

	```
	git check-ignore -v App.class
	```
	
	use `!` to make exceptions
	
	```
	!tolua.lib
        ```
	
### using alias

	```
	git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
	git lg
	```

## How to deal with error

### untracked directory:

* reason: directory included .git file

* solutions: 

	```
	rm -f .git/index.lock  
	git rm --cached <directory>  
	git add <dirctory>  
	```

### connect timeout:  

	```
	ssh: connect to host github.com port 22: Connection timed out
	fatal: Could not read from remote repository.
	```

* reason: could be github's server problem

* solutions:  

	```
	cd ~/.ssh
	vim config
	i
	> Host github.com
	> User loganshi@sjtu.deu.cn
	> Hostname ssh.github.com
	> PreferredAuthentications publickey
	> IdentityFile ~/.ssh/id_rsa
	> Port 443
	:wq
	ssh -T git@github.com //check if reconnect
	```

### push error

	```
	error: src refspec master does not match any.
	```

* solution:
	
	```
	git add . && git commit -m "init"
	``` 

	
