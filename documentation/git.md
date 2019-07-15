# How to use git

## local git repository

	```
	git init <repo_name>
	git add <target_file>
	git commit -m "commit message"
	git clone <repo_name> <target_directory>
	git status
	git diff
	git reflog
	git reset --hard <reflog_id>
	```

## branching

	```
	git branch
	git checkout [branch]
	```
  
## remote git repository

	```
	git remote add [remote_repo_name] [git@github.com:Logan-Shi/multi-robot-mapping.git] 
	git push -u [remote_repo_name] [branch] [-f]
	git remote -v
	```


## How to deal with error

### untracked directory:

* reason: directory included .git file

* solutions: 

	```
	rm -f .git/index.lock  
	git rm --cached [directory]  
	git add [dirctory]  
	```