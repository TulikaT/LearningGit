1. git vs github
        git is a version-control system
        github is an online platform for hosting git repositories and collaborating.
2. the 4 important places
        your files
           ⬇️
        working directory        -> actual project folder
           ⬇️  git add
        staging area             -> Git has an intermediate area called the staging area. we choose which changes should go into next commit.
           ⬇️  git commit
        local repository         -> the staged changes are stored in  local Git repository. This repository exists on our computer.
           ⬇️  git push
        github repository        -> Remote Repository/ GitHub
3. git init                      -> used to convert normal folder into git repository
4. git status                    -> tells about: modified files, untracked files, staged files, current branch, commits ahead/behind remote
5. git add                       -> after modification,  stag one file: git add fileName, or both file: git add file1 flie2, or all file at once: git add .  -> this does not means commit, it puts changes into staging area
6. git commit                    -> after stagging: git add . -> create a commit:  git commit -m "initial commit"  -> git stores the snapshot of different commits hence switching between different commit is possible
                                    commit is essentially a snapshot of project at particular time
7. git add vs git commit
        git add                  -> select changes for next commit
        git commit               -> save stages changes as a git snapshot
8. why not directly commit       -> might modify 5 files but only want 2 for next commit
9. git log                       -> to see previous commits    shorter version: git log --oneline
10. .gitignore                   -> this tells git not to track these files
11. connecting git to github     -> github repo url provided by github when creating a repo, connect it to local repo : git remote add origin github_repo_link
12. check if both connected      -> git remote -v     :     orign repo_link (fetch)   orign repo_link (push)
13. what is origin?              -> simply a name refers to main github repo:  instead of typing complete repo name type: git push origin main -> conviction
14. git push                     -> upload commit from local to github repo: git push origin main
15. git pull                     -> receiving/integrate changes from github repo to local repo current branch: git pull
16. git fetch vs git pull        -> fetch: tell me changes  pull: fetch + merge/integrate changes into local
17. git clone                    -> to get github repo into local computer
18. clone vs pull
        git clone                -> get a repository for the first time : get clone ...
        git pull                 -> Update an existing local repository : git pull
19. branches                     -> to work on different feature different branches can be created and independently working is possible
20. git branch                   -> list all branches, current branch has * sign, create branch: git branch branch_name
21. git switch                   -> git branch does not switch to create branch, to switch: git switch branch_name, create and switch: git switch -c branch_name
22. git checkout                 -> switch to another branch: git checkout branch_name, restore an old version of files, historically git checkout was used for creating,switching, restoring, but now different command used,
23. git switch -c vs git branch
        git branch               -> creates branch only
        git switch -c            -> creates and switches
24. Merging                      -> first switch to main: git switch main, then merge the branches using git merge branch_name
25. merge conflicts              -> if 2 people modify same part of a file, git dint know which version to keep, this should be done manually
26. git rebase                   -> like merge, rebase integrates changes: git rebase main
27. merge vs rebase
        Merge: preserves the branching history
        Rebase: create a more linear history
28. git reset                    -> Moves branch pointer backword. It is mainly used to undo commits or unstage changes, depending on the option you use.
29. git reset --soft HEAD-1      -> undo the last commit, but keep its changes staged.  A---B---C   =>  A---B  but C changes remain staged
30. git reset --mixed HEAD-1     -> undo the last commit, keep the changes in my files, but unstage them i.e C changes remains in local repo
31. git reset --hard HEAD-1      -> undo the last commit, discard changes
32. HEAD                         -> commit before Head, HEAD-1: 1 commit before head, HEAD-2: 2 commit before head
33. git revert:                  -> creates new commit that reverses the old commit: A---B---C  =>  A---B---C---D
34. reset vs revert
        reset                    -> moves history pointer, can rewrite history, dangerous on shared branches, useful for local mistakes
        revert                   -> creates a new commit, preserves history, safer for shared branches, useful for published commits
35. git restore                  -> restore is primarily for restoring file
36. git restore --staged         ->  
        
