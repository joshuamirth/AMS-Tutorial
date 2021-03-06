# AMS Notes on Git

Source for most of this: https://www.atlassian.com/git
Notes available at https://github.com/CrossXProduct/AMS-Tutorial

## Basic Ideas

Git is a Distributed Version Control System.
The basic unit is a _repository_ and its _branches_, and the key operations are _committing_, _pushing_, and _pulling/merging_.

* Repository: A folder containing files and subfolders associated to a project. Git works best with content in the form of text files (think source code, LaTeX files, HTML, or raw data in .csv or similar).
* Git tracks the changes in any folder that is made into a Git repository. But it doesn't track every time a file is written to disk, just when you tell it to add the current state of the folder to its history. This is called a commit.
* Git keeps a log of all the commits, which is the idea of _version control_. You can at any time look at the whole history and reset a project or part of one to where it was at a given time.
* A branch of a repository is a second version of the repository. Usually they are used if you want to experiment with something while maintaining a clean version of your work.
* Different branches can be combined back together in a number of ways (this is where people usually get confused!).
* GitHub (and Bitbucket, Gitlab, et cetera) are online services that let you maintain a branch of your project on a remote server. Most importantly, they allow multiple people to have access to the same repository.

## Usage
Installing on Linux: `sudo apt get install git` (or similar)
Installing on Mac: https://www.atlassian.com/git/tutorials/install-git?section=git-for-mac-installer
Installing on Windows: https://www.atlassian.com/git/tutorials/install-git#windows

### Basic tutorial:
* Open a terminal and a text editor.
* Make a new directory to be your Git repo (best not to have spaces in the name).
* Navigate to that folder in your terminal and run `git init`. This turns the empty folder into a git repository.
* Type `git status`. This tells you the status of your git folder.
* Type some stuff in the text editor. Save it into your repository.
* Run `git status` again. You should now have some info appear.
* Type `git add filename.txt` in your terminal. This command lists `filename.txt` as one of the files ready to be committed.
* Type `git commit`. Your text editor should open. Type a message there, save it, then close it.
* Alternatively, use `git commit -m "your commit message"` if you don't have a lot to say.
* Type `git branch`. You should see something like `* master` displayed. Master is the name of your branch (if you only have one). The star indicates which branch you are using.
* Type `git branch new_branch`. This creates a new branch title `new_branch`.
* Now `git branch` should list two branches, master and new_branch. Switch to new branch with `git checkout new_branch`.
* Make some changes to you file, or add a new file, and make a commit while in new_branch.
* Now `git checkout master` to go back to the original branch. Note that the change you just made does not show up.
* To merge the changes from the new branch into the master branch, run `git merge new_branch`.

You can get the full details of any git command by running `man git-$commandname` in the terminal, where `$commandname` is replaced by the name of the command you want to learn about. In general Google is maybe more helpful, though!

### Interacting with others via GitHub.
* First, go to GitHub and create an account or login if you already have one. (I think that it is beneficial if you use a `.edu` email when you sign up.)
* In your terminal, navigate somewhere other than the git repository you have been working in (say, to your desktop).
* Navigate there and type `git clone https://github.com/CrossXProduct/AMS-Tutorial.git`.
* This is similar to `git init` except instead of making a blank repository, you are creating one that starts as a copy of the one on Github.
* Open your text editor and make a new file with whatever contents you like. Name it `$yourname.txt`. (So everyone makes something with a different name!).
* Save and commit your file.
* **Now, the most important part of this tutorial:** pull the online version of the repository (note: everyone must be added to this repository as user on Github first, otherwise forking and pull requests are required), and then push your commit to it. So run `git pull` to get the current version of the online repository onto your local machine. Then run `git push` to send *your* commit to the server.
* One everyone has made a push, run `git pull` again. You should see a bunch of new files appear.
* Run `git log`. This will show everyone's commit messages.
* (The reason for running `git pull` first is that it keeps a more linear working tree. In particular, if there is a merge conflict, it is easier for you to fix it on your local machine before sending your commits online.)
* Let's handle a conflict: one person edit the file `joshua_mirth.txt` and commit their edit to the repository. I will also make an edit to it.
* If I run a `git push` a warning will appear because the two branches have diverged.
* Instead, I should run `git pull`. This will also give a warning, but it will show me the conflict and allow me to make an edit.
* After editing and fixing it and committing those changes, I can run `git pull` again, to make sure no other changes happened, and then finally push my version.
* Now if everyone runs `git pull` they should get a clean, up-to-date version of the repository.
