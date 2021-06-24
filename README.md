# Git-Basic
Github 유용한 명령어 정리


# Github

**Table of Contents**
* [1. PUSH](#1-push)
  * [1.1 When you push to your own repo](#11-when-you-push-to-your-own-repo)
  * [1.2 When you push to other's repo(especially branch)](#12-when-you-push-to-others-repoespecially-branch)
  * [1.3 When `git push` fails](#11-when-git-push-fails)
  * [1.4 First push from local branch](#14-first-push-from-local-branch)
* [2. Make](#2-make)
  * [2.1 Make folder and file](#21-make-folder-and-file)
* [3. gitignore](#3-gitignore)
  * [3.1 Make .gitignore](#31-make-gitignore)
* [4. Branch](#4-branch)
  * [4.1 Change branch name](#41-change-branch-name)
  * [4.2 Make and checkout to branch](#42-make-and-checkout-to-branch)
  * [4.3 Delete branch](#43-delete-branch)
* [5. Merge](#5-merge)
  * [5.1 Merge branch to master](#51-merge-branch-to-master)
  * [5.2 When conflict occurs](#52-when-conflict-occurs)
* [6. Mirror](#6-mirror)
* [7. Remove](#7-remove)
  * [7.1 Remove directory/file](#71-remove-directoryfile)
* [8. Jekyll - Setting Bundle](#8-jekyll---setting-bundle)

## 1. PUSH

### 1.1 When you push to your own repo             
```console
$ git add *
$ git commit -m "Message"
$ git push
```
You can manually add files like `git add ./README.md`   

### 1.2 When you push to other's repo(especially branch)

```console
$ git remote add origin YOUR_REPO
$ git remote add other OTHER's_REPO

($ git checkout YOUR_BRANCH // Optional)
($ git pull master YOUR_BRANCH // Optional)
$ git push other YOUR_BRANCH
```
### 1.3 When `git push` fails

  ```console
  $ git push --all --force   
  ```
should work

### 1.4 First push from local branch

If you initially push your local repository to the remote repository, there's no setting for tracking that branch. In this case, add `--set-upstream` option to your local branch so that it can track your branch.   
```console
$ git push --set-upstream origin branch_name

# or just

$ git push -u origin branch_name
```
<br/>   

## 2. Make
### 2.1 Make folder and file
```console
$ mkdir directoryName
$ cd directoryName
$ touch .FileName     # e.g. touch .README.md
```
<br/>   

## 3. gitignore
### 3.1 Make .gitignore
`.gitignore` 
```gitignore
# .gitignore

venv/           # folder
README.md       # file with extension
*.exe
```

_**BUT**_ if the file or folder was already pushed before, it'll not work.   
In this case, following should work.   

```console
$ git rm --cached test.txt        # if it's a file,

$ git rm --cached *.txt           # if there are files with the same extension,

$ git rm --cached test/ -r        # if it's a folder, (-r: recursively)
```
<br/>   

## 4. Branch
### 4.1 Change branch name

```console
$ git branch -m old_branch new_branch         # Rename branch locally    
$ git push origin :old_branch                 # Delete the old branch    
$ git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
```

### 4.2 Make and checkout to branch
```console
$ git checkout -b branch_name
```

### 4.3 Delete branch
```console
$ git branch -d branch_name
```
<br/>   

## 5. Merge
### 5.1 Merge branch to master

First, go to your master branch
```console
$ git checkout master
```

Then, merge branch to master
```console
$ git merge branch_name
```

### 5.2 When conflict occurs

You can cancel merging
```console
$ git merge --abort
```
<br/>   

## 6. Mirror

* Set your **`old remote repository`**
  ```console
  $ git remote -v
  ```
* Clone your **`old remote repository`**
  ```console
  $ git clone --mirror https://github.com/example/old_test.git
  ```

* Make your **`New remote repository`** on Github

* Set your **`new remote repository`**
  ```console
  $ git remote set-url --push origin https://github.com/example.new_test.git
  ```
* Mirror old repository to a new one
  ```console
  $ git push --mirror
  ```
<br/>   

## 7. Remove
### 7.1 Remove directory/file
```console
$ rm -r -f -d DIRECTORY_NAME

# or just

$ rm -rdf DIRECTORY_NAME
```
<br/>   

## 8. Jekyll - Setting Bundle

* When you just want to change all the codes without removing repository, run   

    ```console
    $ git init
    $ git add *
    $ git commit -m "Your Comment"
    $ git push --set-upstream origin master --force
    ```

* Then, when you want to run `bundle exec jekyll serve`, but it doesn't work, run

    ```console
    $ bundle init
    ```
    to make a `Gemfile`. If there is no `gem "jekyll"`in `Gemfile`, then add it. And then run

    ```console
    $ bundle install
    ```
    to install bundled gems.

    ```console
    $ bundle exec jekyll serve
    ```
    Then, run above code to run jekyll server.

