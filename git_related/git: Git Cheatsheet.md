[git show and restore a file](https://stackoverflow.com/questions/610208/how-to-retrieve-a-single-file-from-a-specific-revision-in-git)
### ```git show```  
> This command is used to see content of a file from a given previous SHA  
> This command could be useful if you want to peek a previous version of the file or want to revert the changes for a given file  
> ```
> git show object
> git show $REV:$FILE
> git show somebranch:from/the/root/myfile.txt
> git show HEAD^^^:test/test.py
> ```

### ```git restore```  
> This command is useful if you want to resotre a single file from a given SHA  
> ```
> git restore -s <SHA1>     -- afile
> git restore -s somebranch -- afile
> ```


