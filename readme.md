# GIT

- [GIT](#git)
    - [Usefull Overview](#usefull-overview)
    - [Configure Git](#configure-git)
    - [SSH](#ssh)
    - [Create a new local repository](#create-a-new-local-repository)
    - [Branches](#branches)
    - [Add one or more files to staging](#add-one-or-more-files-to-staging)
    - [Commit](#commit)
    - [Push](#push)
    - [Tags](#tags)
    - [Connect to a remote repository](#connect-to-a-remote-repository)
    - [Update from remote repository](#update-from-remote-repository)
    - [Check out a repository](#check-out-a-repository)
    - [Undo local changes](#undo-local-changes)
    - [Tipps](#tipps)

## Usefull Overview

![Git Ebenen](git_ebenen.png)


## Configure Git

### User Config

```bash
$ git config --global user.name "name"

$ git config --global user.email <mail adress>
```

### Set the default Editor

```bash
$ git config --global core.editor "code --wait"
```

## SSH

### SSH Key für Github.com generieren

```bash
$ ssh-keygen -t ed25519 -C "adress@server"
```

### Kopieren des SSH-Keys in den Zwischenspeicher und bei Github einfügen

```bash
$ clip < ~/.ssh/id_ed25519.pub
```

### SSH Zugang Testen & Fingerprint vergleichen:

```bash
$ ssh -T git@github.com
```

    SHA256:uNiVztksCsDhcc0u9e8BujQXVUpKZIDTMczCvj3tD2s (RSA)
    SHA256:br9IjFspm1vxR3iA35FWE+4VTyz1hYVLIE2t1/CeyWQ (DSA – veraltet)
    SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM (ECDSA)
    SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU (Ed25519)



## Create a new local repository
```bash
$ git init
```

## Branches 

### rename master to main
```bash
$ git branch -M main
```

### 1. Create a new branch and switch to it:   
```bash
$ git checkout -b < branchname >
```

### 2. Switch from one branch to another:
```bash
$ git checkout < branchname >
```

### 3. List all the branches in your repo, and tell you what branch you’re currently in:
```bash
$ git branch
```

### 4. Delete the feature branch:
```bash
$ git branch -d < branchname >
```

### 5. Push all branches to your remote repository:
```bash
$ git push --all origin
```

### 6. Push a branch into your remote repository:
```bash
$ git push origin :< branchname >
```

## Add one or more files to staging
```bash
$ git add < filename > git add *
```

## Commit

### Commit changes to head:
```bash
$ git commit -m "Commit message"
```

### Commit any files you’ve added with git add, and also commit any files you’ve changed:
```bash
$ git commit -a -m "message"
```

## Push

### Send changes to the master branch of your remote repository:
```bash
$ git push origin master
```

## Tags

### 1. You can use tagging to mark a significant changeset, such as a release:
```bash
$ git tag 1.0.0 < commitID >
```

### 2. **CommitId** is the leading characters of the changeset ID, up to 10, but must be unique.
### Get the ID using:

```bash
$ git log

$ git log --oneline
```

### 3. Push all tags to remote repository:

```bash
$ git push --tags origin
```

## Connect to a remote repository

### If you haven’t connected your local repository to a remote server, add the server to be able to push to it:

```bash
$ git remote add origin < server >
```

### List all currently configured remote repositories:
```bash
$ git remote -v
```

## Update from remote repository

### 1. Fetch and merge changes on the remote server to your working directory:
```bash
$ git pull
```

### 2. To merge a different branch into your active branch:
```bash
$ git merge < branchname >
```

### 3. View all the merge conflicts:
```bash
$ git diff
```

### 4. View the conflicts against the base file:
```bash
$ git diff --base < filename >
```

### 5. Preview changes, before merging:
```bash
$ git diff < sourcebranch > < targetbranch >
```

### 6. After you have manually resolved any conflicts, you mark the changed file
```bash
$ git add < filename >
```

## Check out a repository

### Create a working copy of a local repository
```bash
$ git clone /path/to/repository
```

### For a remote server, use: 
```bash
$ git clone xx@host:/path/to/repository
```

## Undo local changes

### 1. You can replace the changes in your working tree with:
```bash
$ git checkout -- < filename >
```

### 2. To drop all your local changes and commits, fetch the latest history from the server and point your local master branch at it, do this:
```bash
$ git fetch origin git reset --hard origin/master
```

## Tipps

- Nicht zu viel Zeit lassen bis zum Pull request damit sich nciht zu viele Changes aufstauen
- Locales mergen von remotechanges in main in eigene branches um mit aktueller Version zu arbeiten
- mit Team absprechen das es pullrequests gab auf main und jeder seinen working branches updated
- dav als mein branch nutzen und nur sichere änderungen in main mergen, (second layer of protection)

