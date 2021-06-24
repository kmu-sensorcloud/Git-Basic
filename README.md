# Git-Basic
Github 유용한 명령어 정리


# Github

**ABSTRACT**   
Of the git, by the git, for the git

## 1. PUSH

* **When you push to your own repo**              
  ```console
  $ git add *
  $ git commit -m "Message"
  $ git push
  ```
  You can manually add files like `git add ./README.md`   

* **When you push to other's repo(especially branch)**   

  ```console
  $ git remote add origin YOUR_REPO
  $ git remote add other OTHER's_REPO

  ($ git checkout YOUR_BRANCH // Optional)
  ($ git pull master YOUR_BRANCH // Optional)
  $ git push other YOUR_BRANCH
  ```


## 2. When `git push` fails

  ```console
  $ git push --all --force   
  ```

should work

## 3. Make folder and file
  ```console
  $ mkdir directoryName
  $ cd directoryName
  $ touch .FileName     # e.g. touch .README.md
  ```

## 4. `.gitignore` 
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

## 5. Branch

* **Change branch name**   

  ```console
  $ git branch -m old_branch new_branch         # Rename branch locally    
  $ git push origin :old_branch                 # Delete the old branch    
  $ git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
  ```

* **Make and checkout to branch**   
  ```console
  $ git checkout -b branch_name
  ```

* **Delete branch**   
  ```console
  $ git branch -d branch_name
  ```

* **First push from local branch**

    If you initially push your local repository to the remote repository, there's no setting for tracking that branch. In this case, add `--set-upstream` option to your local branch so that it can track your branch.   
    ```console
    $ git push --set-upstream origin branch_name

    # or just
    
    $ git push -u origin branch_name
    ```

## 6. Merge

* **Merge branch to master**   

  First, go to your master branch
  ```console
  $ git checkout master
  ```

  Then, merge branch to master
  ```console
  $ git merge branch_name
  ```

* **When conflict occurs**   

  You can cancel merging
  ```console
  $ git merge --abort
  ```

## 7. Mirror

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

## 8. Remove directory/file

```console
$ rm -r -f -d DIRECTORY_NAME

# or just

$ rm -rdf DIRECTORY_NAME
```

## 9. Jekyll - Setting Bundle

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

