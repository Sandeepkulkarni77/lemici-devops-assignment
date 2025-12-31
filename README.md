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
2-does not change you local branch,updates only remote tracking branch. Ex- origin/main. 
3-provides more control, you can inspect the changes before deciding to integrate them. 
4-does not cause conflicts. 
5-use when you want to review the updates safely without integrating it to your current work or simply check what others have been doing. 

git pull: 
1-Download and then merges new data into your current working branch. 
2-updates local branch immediately. 
3-less control, because the integration is automatic and immediate which may lead to conflicts. 
4-can cause merge conflicts if there are conflicting changes between your local and remote branch.
5-use when you want to quickly synchronize your local branch and are confident the won't cause major conflicts. (ex - working solo or on a fast paced project). 


#Task-3 
How would u resolve a git merge conflict(example scenario)
1-A merge conflict can occur when two branches modify the same line of a file in different ways. 
2-for example, two feature branches may update the same configuration value in a shared file. 
3-when the first branch is merged into the main branch, it succeeds because there is no conflict at that point.
4-however, when the second branch is merged, git is unable to automatically decide which change should be kept, since both changes affect the same line,in such cases, git pauses the merge and marks the conflicting sections in the file.
5-to resolve the conflict, the file is reviewed manually, the conflicting changes are analyzed, and a meaningful final version is created by keeping or combining the required changes.
6-once the file is corrected, it is staged and committed, which completes the merge process.


