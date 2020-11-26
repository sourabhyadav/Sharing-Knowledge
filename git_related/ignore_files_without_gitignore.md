### How to ignore local files without putting them in .gitignore files?  
You can add the files to be excluded to ```.git/info/exclude``` file. This is similar to ```.gitignore``` but you need not to push this file on server. This will avoid the files to get staged.  

Use-case [link1](https://www.jerriepelser.com/blog/exlude-git-files-locally/) and [Link2](https://medium.com/@dave_lunny/exclude-files-from-git-without-committing-changes-to-gitignore-986fa712e78d)
