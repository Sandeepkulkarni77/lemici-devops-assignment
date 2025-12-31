Part-1: 
#Task-1
1-Repository was set up using SSH authentication. 
2-SSH keys were generated locally and the public key was added to GitHub.  
3-Repository was cloned using the SSH URL.
4-Git operations work without username/password, confirming SSH setup.

#Task-2
git fetch vs git pull 
git fetch:
1-Downloads new data from remote repo(commits,files).
2-Does not change you local branch,updates only remote tracking branch. Ex- origin/main. 
3-Provides more control, you can inspect the changes before deciding to integrate them. 
4-Does not cause conflicts. 
5-Use when you want to review the updates safely without integrating it to your current work or simply check what others have been doing. 

git pull: 
1-Download and then merges new data into your current working branch. 
2-Updates local branch immediately. 
3-Less control, because the integration is automatic and immediate which may lead to conflicts. 
4-Can cause merge conflicts if there are conflicting changes between your local and remote branch.
5-Use when you want to quickly synchronize your local branch and are confident the won't cause major conflicts. (ex - working solo or on a fast paced project). 


#Task-3 
How would u resolve a git merge conflict(example scenario)
1-A merge conflict can occur when two branches modify the same line of a file in different ways. 
2-For example, two feature branches may update the same configuration value in a shared file. 
3-When the first branch is merged into the main branch, it succeeds because there is no conflict at that point.
4-However, when the second branch is merged, git is unable to automatically decide which change should be kept, since both changes affect the same line,in such cases, git pauses the merge and marks the conflicting sections in the file.
5-To resolve the conflict, the file is reviewed manually, the conflicting changes are analyzed, and a meaningful final version is created by keeping or combining the required changes.
6-Once the file is corrected, it is staged and committed, which completes the merge process.

#Task-4 
Resolving a git merge conflict (practical demonstration)
1-In this task, a merge conflict was intentionally simulated using two feature branches created from the same base commit,a configuration file (config.yaml) was added to the main branch containing basic application settings, including a log_level parameter.
2-Two branches, feature-A and feature-B, were created from the same version of the main branch.
3-In feature-A, the log_level was updated to debug to represent a development or debugging requirement.
4-In feature-B, the same log_level was updated to error to represent a production-focused change. Since both branches modified the same line in the same file differently, a conflict was guaranteed when merging.
5-The feature-A branch was merged into main successfully because no competing change existed at that time.
6-When feature-B was merged into main, Git detected conflicting changes in config.yaml and stopped the merge process.
7-The conflicted file was then opened on the main branch, conflict markers were removed, and a meaningful final value was chosen for the log_level.
8-After resolving the conflict, the file was staged and committed with the message “Resolved merge conflict in config.yaml”, which completed the merge process.
9-This demonstrated a real-world merge conflict scenario and manual conflict resolution using git.

