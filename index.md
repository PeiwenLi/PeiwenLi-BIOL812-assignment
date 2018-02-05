# Question 1
**When should you use Git for a project?**
* When you would like to share your project with others, and get inputs from them (more than 1 developers working on the same project);
* When you would like to back-up your project, including every changes you and your co-workers will make to them for future reference (version control);

# Question 2
**What kind of files/info should be saved in a Git repository? What types of files/info should not be included in a Git repo?**
* Should: text-based files/info that you would like to share with others (open source). For example, codes, scripts etc.
* Should not: files/info that contain sensitive message and large-sized files. For example, private data file that hasn't been published.

# Question 3
**What are the commands to undo a commit?**    
There are at least four ways to do this, depending on what you want to do:
1. This help you to go back to the x-number of commits counting back from the head, and make changes from there without losing commits in between.
```{r}
# If you would like to go back to the 4th commit, which added a line "123" to the file "mars.txt"
> git checkout HEAD~4 mars.txt
> git commit -m 'commit_name'
> git log
# You can see a new commit called 'commit_name'
> nano mars.txt
# You can see the line "123" in "mars.txt"
```
2. This evicts the last commit from the branch and from the index, but leave the working tree around (keep the changes in the file for reworking, but remove the commit from the log)
```{r}
> git reset HEAD^
```
3. This removes the last commit from git and also discards the changes you made in the file
```{r}
> git reset --hard HEAD^
```
**Be careful with the `--hard` command: this can at the same time throw away all your uncommitted changes in your working directory**       
If you are removing multiple commits from the top, you can run this:
```{r}
# to remove the last x-number of commits
> git reset --hard HEAD~x
```
4. This reverts commit(s) from git, leaves a new entry in log, and discards the changes you made   
```{r}
> git revert [--no-edit] <commit_ID>
```
# Queestion 4
**One of your repositories is in a “detached HEAD” state. How do you fix this?**
```{r}
git checkout master
```

# Question 5
**Your boss has no idea what Git is or why you are using it. Explain the pros / cons of using Git for your research project. Explain the pros / cons of hosting your project in a public (or private) repository on Github/Bitbucket/Gitlab/etc.**    
*Using Git:*
* Pros:
  + Supports version control of your work
  + Allows you to keep tracking changes in your work
  + Allows you to undo changes
  + Good place for info/files storage
* Cons
  + Takes some time for one to understand and get familiar with Git
  + Cannot store large-sized files     

*Using public repository:*
* Pros:
  + Allows multiple developers to work on the same project
  + Provides a place to share your work/knowledge with other people
* Cons:
  + If you want to make the repository private, you ususally have to pay
  + Poses a risk of sharing your privite work/info
