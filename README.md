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
17.  
        
