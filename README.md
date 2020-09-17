# Git

1.To know the parent branch 
 
 	
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



2.To Get rid of 
"please enter a commit message to explain why this merge is necessary, especially if it merges an updated upstream into a topic branch."

	press "i"
	write your merge message
	press "esc"
	write ":wq"
	then press enter

3.Fetch from upstream
	
	git fetch upstream
	git merge upstream/master master

4.Clone a New Repo

	git clone git@github.com:kvallieur/project-details-service.git
	git remote add upstream git@github.com:MerrillCorporation/user-service.git
	git remote -v should result in
		origin	git@github.com:kvallieur/user-comp-service.git (fetch)
		origin	git@github.com:kvallieur/user-comp-service.git (push)
		upstream	git@github.com:MerrillCorporation/user-comp-service.git (fetch)
		upstream	git@github.com:MerrillCorporation/user-comp-service.git (push)

5.Create a new Branch in local and remote

	git checkout -b xxxxxxx
	Git push origin xxxxxxx

6.Delete a branch

	To delete a branch in local = git branch -d xxxxxxxx
	To delete in both local and remote = git push xxxxx —delete xxxxx

7.Creates a branch in the fork from Headless 

	git checkout --track origin/user-combined

8.Stash Untracked
	
	git stash --include-untracked

9.Remove unwanted commits
	
	git reset --hard [$sha1 commit]
	git push -f       #this is force push will not show up in history

Golden Rule
	Never rebase shared commits
	Never erase shared history

10.Squash Commits

	Git rebase -i
	replace pick with squash

11.Use git commit —amend if you wish to change just the previous commit

12.Cherry Pick example

	So, I had a pull request introducing the log component. I went to the pull request in GitHub and pulled the branch down (using the "use the command line" directions, but I could've also pulled down with the GitHub UI.)
	On the command line, I then ran git checkout master. I went to the GitHub UI, found the commit I wanted, and grabbed its commit hash by clicking the little "copy" icon next to it in the commit list. Then I ran git cherry-pick long-hash-here-pasted-from-github.
	Finally, I pushed it up to GitHub with git push origin master. Done! Finally, I closed the pull request manually with a link to the commit.

	Here's the entire process:
		git fetch origin
		git checkout -b add-log-component origin/add-log-component
		git checkout master
		git cherry-pick COMMIT-HASH-HERE
		git push origin master



13.Remove DS_Store files
 
 	find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch

13.Shows the output of git log and git branch concisely

	git config --global --replace-all core.pager "less -F -X"


	
