**1.How to change commit name.**  
Answer: To change the commit message, you can use the --amend option with the git commit command. The --amend option allows you to make changes to the most recent commit message. For example: git commit --amend -m "New commit message" This will open your default text editor to modify the commit message. You can also include the new message with the -m option, as shown in the example.to force push your changes to the remote repository.git push --force origin yourBranch

**2.git actions default action**  
Answer:  
**3.Explain about gitlab runners and types    
Answer:** GitLab Runner is an application that works with GitLab CI/CD to run jobs in a pipeline.  
There are three types of runners, based on who you want to have access:  
Shared runners are for use by all projects  
Group runners are for all projects and subgroups in a group  
Project runners are for individual projects  

**4. Git pull vs git fetch    
Answer:**  git fetch updates your remote-tracking branches under refs/remotes/<remote>/. This operation is safe to run at any time since it never changes any of your local branches under refs/heads.  
git pull brings a local branch up-to-date with its remote version, while also updating your other remote-tracking branches.  
git pull runs git fetch with the given parameters and then depending on configuration options or command line flags, will call either git rebase or git merge to reconcile diverging branches.  

**5. Define Git stash**  
Answer:  git stash temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. Stashing is handy if you need to quickly switch context and work on something else, but you're mid-way through a code change and aren't quite ready to commit.
**6. How to 20 commits into a single commit **  
Answer:    
**7. what is git tag**  
**Answer:** Tags are ref's that point to specific points in Git history. Tagging is generally used to capture a point in history that is used for a marked version release (i.e. v1.0.1). A tag is like a branch that doesn’t change. Unlike branches, tags, after being created, have no further history of commits.  
 
 **git tag <tagname>**  
 A tag is used to label and mark a specific commit in the history.    
It is usually used to mark release points (eg. v1.0, etc.).    
Although a tag may appear similar to a branch, a tag, however, does not change. It points directly to a specific commit in the history and will not change unless explicitly updated.  

**8.what is git rebase?  
Answer:** Rebasing is the process of moving or combining a sequence of commits to a new base commit. Rebasing is most useful and easily visualized in the context of a feature branching workflow.   
**git rebase <base>**   
**9.What is git-cherry-pick? why we use it?    
Answer**   Cherry-picking in Git means choosing a commit from one branch and applying it to another.    
It's also possible to cherry-pick multiple commits but merge is the preferred way over cherry-picking.  
Make sure you are on the branch you want to apply the commit to.  
**git switch master**
Execute the following:  
**git cherry-pick <commit-hash>**  

**10.What is a conflict in git?    
Answer**  Conflicts generally arise when two people have changed the same lines in a file, or if one developer deleted a file while another developer was modifying it. In these cases, Git cannot automatically determine what is correct. Conflicts only affect the developer conducting the merge, the rest of the team is unaware of the conflict. Git will mark the file as being conflicted and halt the merging process. It is then the developers' responsibility to resolve the conflict.  
**11.What is git reset ? Types of reset ?   Answer**   
**12.what is the importance .git directory?    
Answer**   The .git directory in a Git repository is a critically important component of the repository's structure. It contains all the information and metadata that Git needs to manage the repository, track changes, and facilitate version control.  
**13.What PR (Pull request) is? whats the importance of PR?  
Answer** A pull request – also referred to as a merge request – is an event that takes place in software development when a contributor/developer is ready to begin the process of merging new code changes with the main project repository.  
During a pull request, the repository maintainer reviews new code updates from a developer to determine whether or not it is ready to be released. Without pull requests, unfinished or incorrectly written code updates could be prematurely merged with the main repository and break or cause issues with the live product.  

**14.What is git squash?    
Answer**Squashing commits in Git refers to the process of combining multiple consecutive commits into a single commit. This is typically done to clean up the commit history, especially before merging a feature branch into the main branch (e.g., master). Squashing makes the commit history more concise and easier to understand.  
**15.Branching strategy?   
Answer** https://www.bmc.com/blogs/devops-branching-strategies/ 
