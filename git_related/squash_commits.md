## How to sqaush multiple commits into single clean commit  

Many a times it happens that while developing code we tend to commit multiple changes to our branch. Sometimes these commits are very small but it keep on populating our commit history. Example variable name changed, code reformatting, obvious bug fixing, default variable etc.  

So at the end of each day or end of a particular feature a developer should consider to squash commits before pushing his changes.  

```
git rebase -i HEAD~5
```  
* ```HEAD-5``` you want to squash last 5 commits into single.
* You will be prompted to a vim editor to pick n suash from those commits  

[Detail Descriptioin](https://stackoverflow.com/questions/3233056/how-do-i-avoid-committing-small-changes-in-git)