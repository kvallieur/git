# Git

To know the parent branch 
 
 	
	git show-branch -a \
	| grep '\*' \
	| grep -v `git rev-parse --abbrev-ref HEAD` \
	| head -n1 \
	| sed 's/.*\[\(.*\)\].*/\1/' \
	| sed 's/[\^~].*//'
 
 Will give you develop if you run it from H and master if you run it from I.
 
    A---B---D <-master
      \
       \
        C---E---I <-develop
             \
              \
               F---G---H <-topic
