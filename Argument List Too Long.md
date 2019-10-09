# Argument List TOo Long Error in Linux

Have you  faced this error while writing shell  scripts? For e.g. simpile command like rm *.txt, cp *txt dst/ etc. can throw this error.

**Reason**:
It orrcurs because of ARG_MAX contant for each command-line arguments. The main problem is the use of "*" there. As you know linux expands the "*" into complete command argument and make intermediate expanded command-line stuff. 
Now this expanded command can go over limit than ARG_MAX allowed. Thus, the error occurs.

**Solution**:

**1. Use For Loop:**
$ for f in /your/path/*txt; do rm $f; done
$ for f in /your/path/*txt; do cp $f dst/; done

**2. Use find command:**
$ find . -maxdepth 1 -name '*.pdf' -delete 

I prefer **Option 1** because it easy to read aAlthough it might be slower that option 2.
