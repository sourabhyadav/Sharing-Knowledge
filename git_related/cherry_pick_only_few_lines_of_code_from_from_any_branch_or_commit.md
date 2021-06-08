## How to pick only a few lines of code from any commit or any branch  

```
# move to the branch you want to merge the code say main
git checkout <main branch to get new code>  
git checkout -p <commit SHA from where the code needs to be taken>  
```  
* This will open a vim editor for each hunk of code to be added or not. 
* You have to press ``y``` or ``n``` for accepting that code code snippet or not  

* Note: the merged code will directly go to stashing stage means you need not to run ```git add``` for this.  

Better approach is:  
```
git cherry-pick -n <commit> # get your patch, but don't commit (-n = --no-commit)  
git reset                   # unstage the changes from the cherry-picked commit  
git add -p                  # make all your choices (add the changes you do want)  
git commit                  # make the commit!  
```  

[link](https://stackoverflow.com/questions/1526044/partly-cherry-picking-a-commit-with-git)