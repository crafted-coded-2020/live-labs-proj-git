:beginner: **setting up git**  

:point_right: git-hub `account name`  
- example : `live1-git-vishesh`
- example : `live2-git-carlos`
- example : `live2-git-prashant`

:point_right: repository 1

- `repository` name : `labs-proj`

- `module folder` : `adv-java` (lab solutions + project solution)

:point_right: repository 2
- `repository` name : `adv-java`

---

:beginner: **Set up git**  

:point_right: setting up github  

1. create an emailid (preferrably gmail)
2. create repository `adv-java`

:point_right: setting up local repository

1. git for windows (git bash)

`cloning the repository`
```sh
git clone "https://github.com/live-git-subbus/labs-proj.git"
```

`add content` 

2. add all the folder `adv-java` (don't tamper .git file)

`push changes from local repository to github` 

3. push the changes from git local repository to github

`configuring git user`
```sh
   git config --global user.name live-git-subbus
```
`add, commit (local repo) and push (remote repo)
```sh

    git add .
    # git commit -a -m "$1"
    git commit -a -m "."
    git push
```

