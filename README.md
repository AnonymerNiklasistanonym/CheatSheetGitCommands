# CheatSheetGitCommands

Some useful commands when working with Git

---

This is neither a professional tutorial nor one of the best ones out there. I just tried to create a simple and quick cheat sheet for new users and myself for the essential and some other cool Git commands I use and have used.

[If you want to learn more look down here to find other great and cool articles/cheat sheets/and more about git.](#resources)

---

<br>

## What is Git and why do so many people use it?

> Git is a [free and open source](https://git-scm.com/about/free-and-open-source) distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

https://git-scm.com/

Version control means that it tracks changes of computer files.

> Git was created by Linus Torvalds in 2005 for development of the Linux kernel, with other kernel developers contributing to its initial development.

https://en.wikipedia.org/wiki/Git

This means that it can not only track your small 1Mb personal project but also really big projects with thousands of files and thousands of people that maintain/work on it without speed issues or hiccups when there are file conflicts ("merge-conflicts").

---

Git is because of it's abilities to be:

* secure,
  (example: Every commit is hashed - you can always be sure this was your commit or this was not your commit)
* not central distributed,
  (example: Everybody that is working on a Git project has a full backup of the whole project)
* flexible,
  (example: You or a group of contributors can just take the project, work on a feature and if you are ready push it to the master project without conflicting with the master project in the time you work on your feature)
* performant
  (example: There are no boundaries in contributors or contributions - everything is handled lightning fast and conflicts are corrected and calculated in milliseconds)
* [and has even more features]

nowadays the most widely used modern version control system in the world.

## Install (G)it

1. Download Git from the official website: https://git-scm.com/downloads
2. Install it when you use macOS or Windows (Linux installs it automatically with `apt-get`)

*Eventually reboot Windows or restart CMD if you can't use Git with CMD.*

## Setup your name/email

Open the new installed command line interface *Git Bash*.

**Global setup:**

```bash
$ git config --global user.name "Your username"
$ git config --global user.name
Your username
$ git config --global user.email "youremail@address.com"
$ git config --global user.email
youremail@address.com
```

**Setup for one repository:**

Use the same commands as above but remove everywhere the ``--global`` parameter.

## Quick explanation of the Git workflow

The main and simple thought/structure behind Git is that you are always in a folder which is the so said **repository**.

In this repository you work on a so said **branch**.

On a branch you can **commit** changes which nothing other than making for everybody (or better said the repository) your specific changes permanent.

This is done with **add**ing **unstaged** files (= files that are different compared to the latest commit) and make them **staged** files. After a commit all staged files are normal files (they are not staged any more because they are no different to the latest commit).

When there are changes from different people on the same file/s on the same parts you can **merge** these changes to a file that makes sense.

Also you can create other branches and work on them without conflicting or doing anything on the **master** branch which is the main branch of each repository and the one you are on per default.

Not only files can be merged but also branches.

---

You can imagine every commit as a point with a unique ID and each branch as a horizontal line on which the commits are placed.

You can without problems combine the points, rename them, delete them or revert all changes to a point without any problems.

Also you can create a connection to a new horizontal line from every commit which automatically contains all the commits before this commit and this commit. From each horizontal line you can later go back to the line where the original commit that created the branch came from and merge all the changes of both branches/lines.

You can do even more things with the lines and points but these are the basics.

<br>

## Essential commands

| Command                     | Explanation                              |
| --------------------------- | ---------------------------------------- |
| `git init`                  | To create a Git repository use this command to set Git up. After running this command the directory in which you ran this command is a Git repository. |
| `git clone URL`             | To clone a local repository use `git clone /path/to/your/repo `. To clone a Git repository from a remote server like `github.com` use `git clone username@host:/path/to/repo`. |
| `git pull`                  | Download the current repository (all the commits from it). |
| `git push`                  | Push all your created commits to the repository. |
| `git status`                | Get a report of which files are *unstaged* or not *pushed*. |
| `git add` + `parameter`     | Stage files for your next commit: That means that every file you add that was before in `git status` unstaged will be committed in your next commit. You can add everything `git add .` or add a specific file `git add unstaged_file` or even add more than one `git add file1 file2 file3`. |
| `git reset` (+ `parameter`) | Reset everything you have done with `git add` before committing (= unstage all staged commits). If you only want to remove a specific file (or more than one) add the file as a parameter: `git reset staged_file`. |
| `git commit` + `parameter`  | Commit your changes. To add a title use the parameter `git commit -m "Your title"` . To add a description use the command two times like this: `git commit -m "Your title" -m "Your descripton"`. If you want to commit all your changes simply add the parameter `-a` to automatically stage all unstaged changes: `git commit -a -m "Your title"`. |

<br>

### `git merge`

When there are conflicts between files when you push something to the *main* repository (which happens very often) or merge branches there is an easy way to **merge** the files:

It first looks very complicated but in the end it's a very simple pattern that looks like this:

```` 
<<<<<<< HEAD
This is text from the original repository.
=======
This is the local text that was pushed or from a branch.
>>>>>>> Branch name or something else
````

To solve the merge edit these lines like they should be (remove on version if wanted or add both or do something different).

This for example would remove the text from the *main* repository:

````
This is the local text that was pushed or from a branch.
````

and this would add both text parts:

```
This is text from the original repository.
This is the local text that was pushed or from a branch.
```

Very easy and simple.

Do this with all merge conflicts (all these patterns) till there are no conflicts any more and then commit and push the changes.

<br>

## Git Bash Vim (Command line text editor)

If you work with the original Git console that came with the installer (at least on Windows) and you use a command like `merge` (and there are conflicts) or `rebase` Git will open the file to control the respective function that should be done not "outside" the console with your default text editor but with the command line editor named Vim.

It probably looks and feels like it makes no sense at all when it suddenly pops up in the command line and you have never encountered or used it. But it is a very easy to use and efficient text editor as soon as you know how to edit text and save files. :smile:

If you have no experience with Vim like I had when I started with Git there is a simple solution to learn how it works in about 10 to 20 minutes: [Just visit this website and do the tutorial. After this you should know the basic things about how to play or even work with vim ;)](http://www.openvim.com/)

### Essential commands in vim

| Command                       | Function                                 |
| ----------------------------- | ---------------------------------------- |
| `i`                           | Go into insert mode from the normal read mode/command mode at the start (edit the file like a normal text file) |
| `ESC`                         | Go back into read mode/command mode      |
| `x`                           | COMMAND-MODE: delete currently selected character (the one after the cursor) |
| `u`                           | COMMAND-MODE: undo the last command      |
| `CTRL` + `r`                  | COMMAND-MODE: redo the last command      |
| `:w` (+ `filename`) + `ENTER` | COMMAND-MODE: save the file under the name `filename` or just save the file if it already exists |
| `:q` + `ENTER`                | COMMAND-MODE: quit/close vim >> Use `:wq` + `ENTER` to save the file and close vim in one command >> Use `:q!` + `ENTER` to forcefully close vim without saving any changes. |

<br>

## Helpful essential commands

| Command                                  | Explanation                              |
| ---------------------------------------- | ---------------------------------------- |
| Undo/Remove your last commit             | You can use the command `git reset --soft HEAD~1 `.  This will rewind your current HEAD branch to the commit one behind the current one which makes the latest commit undone. If you would use `--hard` instead of `--soft` this will throw all the changes away/delete them. Instead of using `HEAD~#` you can also use the hash of the commit to which everything should be made undone. |
| Forcefully push changes because you do not want to merge | Very simple: Just use ` git push -f origin` to commit your current changes with force (only do this if there is no other way -> always try to merge first). |
| Create a new branch                      | `git checkout -b nameOfNewBranch` creates instantly a new branch and automatically moves you onto it. |
| Switch to a branch or back to master     | `git checkout nameOfBranch` switches your onto the branch you add as parameter. To get back to the master branch use the command `git checkout master`. |
| Merge branches                           | With `git merge nameOfBranch` you can merge a branch with the master branch. |
| Connect the repository to `github.com`   | First go to `github.com`, login with your username and create a new repository without a README file. Go back to the console and run command `git remote add origin git@github.com:username/new_repo_name` . Then run`git push -u origin master` to push all your local changes to `github.com`. |

<br>

## More advanced commands

| Command              | Explanation                              |
| -------------------- | ---------------------------------------- |
| Combine/Edit commits | There is a really cool thing called `git rebase -i HASH_OF_COMMIT`. If you use this command it will reset the repository to the commit with the hash you inserted. After this you will get a text document where all the commits after this commit are listed. You can now manipulated each of these commands with changing the first character before the commit ID. Use `e` to edit the commit title/description. Use `d` to completely drop the commit as if it has never existed. If you want to combine commits add to the latest commit of the ones you want to combine a `r` to edit the text and change the part before the ID of all the following commits that you want to combine to `f`. There are many more things you can do but when you done just save and quit this file and the rebase will be started. |

<br>

## <a name="resources"></a>Sources and resources - Learn more:

* [The official git documentation](https://git-scm.com/documentation)
* **[Git cheat sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf) from [GitHub](https://github.com/)**
* [Git help search](https://help.github.com/) from [GitHub](https://github.com/)
* [Start a new git repository](http://kbroman.org/github_tutorial/pages/init.html) from [Karl Broman](http://kbroman.org/)
* [Contribute to someone's repository](http://kbroman.org/github_tutorial/pages/fork.html) from [Karl Broman](http://kbroman.org/)
* [Handling merge conflicts](http://kbroman.org/github_tutorial/pages/merge_conflicts.html) from [Karl Broman](http://kbroman.org/)
* [Amend the last commit message](http://kbroman.org/github_tutorial/pages/amend_commit_msg.html) from [Karl Broman](http://kbroman.org/)
* [Exploring code and its history](http://kbroman.org/github_tutorial/pages/exploring_code.html) from [Karl Broman](http://kbroman.org/)
* [Branching and merging](http://kbroman.org/github_tutorial/pages/branching.html) from [Karl Broman](http://kbroman.org/)
* **[git - the simple guide](http://rogerdudler.github.io/git-guide/) from [Roger Dudler](http://www.twitter.com/rogerdudler)**
* [Learn Git with Bitbucket Cloud](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud) by [Bitbucket](https://bitbucket.org/product)

<br>

## Helping programs

* [GitHubDesktop](https://desktop.github.com/) from [GitHub](https://github.com/) (Windows, macOS) - A great program which you can use for all essential Git things. If you want to do something more advanced just use the original Git console. They work really good together.
* [FastHub](https://play.google.com/store/apps/details?id=com.fastaccess.github&hl=en) from [k0shk0sh](https://github.com/k0shk0sh/FastHub) (Android) - A great Android Client for GitHub on the go (Issues/Discussions/Review of pull requests and more).

<br>

## Ideas, Problems?

If you have any questions/problems or a idea how to make this *cheat sheet* even better just open an issue or a pull request :)