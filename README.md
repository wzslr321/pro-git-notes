<h1 align="center"> Git notes based on book: "Pro Git" by Scott Chacon</h1>

<p align = "center">
  <i>
     This repository contains my personal notes about git that I wrote  while reading a 
     "Pro Git" book. I try to summarize the most important things and organize them properly
     to make it easily accessible whenever needed!
  </i>
</p>

---

<h3> List of content:</h3>

* Basics
* Branching

---

<p align="center">
  Found it useful? Want more updates?
</p>

<p align = "center">
  <b> <i> Show your support by giving a :star:  </i> </b>
</p>

---

<h2 align="center"> Basics </h2>

# 

Two approaches of initializing repository are: 

1. Take an existing project or directory and imports it into Git.
2. Clone an existing Git repository from another server

<h4> Initializing a repository in an existing directory </h4>

- `git init` creates a new subdirectory `.git` that contains all repository files. 
- After fresh initialization, there is nothing tracked yet. 
- To track files use `git add`
    * `git add` can take regular expressions as an arguments, for example: `git add *.dart` adds every dart files. 
    * It can also just take a filename as argument, `git add LICENSE`
  
- With files added, it is possible to make a commit:
   * `git commit -m 'initial commit`
  * `-m` parameter stands for `message`
  
- To get a copy of already existing repository use `git clone` command with url of repo as an argument.
  * `git clone https://github.com/wzslr321/git-notes.git` creates `git-notes` repository and copies the 
  content inside it. It can be overwritten by a name passed after url argument: `git clone <url> notes`-
  creates "notes" directory.

<h4> The lifecycle of status of files </h4>

- Check the status with `git status` command
  * Use `-s` parameter to simplify output

<h4> Ignore files </h4>
* When you've got a file like .env with secret keys, or .js files generated from .ts, you probably want 
git to omit them. To do so, use `.gitignore`
  
* Rules for the patterns in .gitignore file:
  * Blank lines or lines starting with # are ignored.
  * Standard glob patterns work.
  * You can end patterns with a forward slash (/) to specify a directory.
  * You can negate a pattern by starting it with an exclamation point (!).
  
* For example : `*.[abc]` ignores every file that ends with `.a` or `.b` or `.c`.   
  * `*` matches zero or more characters
  * `[]` matches any character inside the brackets
  * `?` matches a single character
  * `([])` matches any character between those specified in `[]`.
  * `**` Matches nested directories. 
  * `!` Make an exception for this file - do not ignore it. 

<h4> View staged and unstaged changes </h4>

 * `git diff` compares what is in your working directory with what is in your staging area. 
* To show the difference between staged files and last commit use `git diff --staged`

<h4> Removing files </h4>

There are 2 ways to remove files from a git: 
  * Remove from working directory
    * remove file from the directory, then remove from a git with: ` git rm <file>`
  * Remove only from staging area
    * `git rm --cached <file>` (To remove everything it is possible to use `.` as argument)

<h4> View commit history </h4>

  * `git log` without any arguments shows every commit of that repository.
  * `-<n>` argument, where `n` is an integer, shows only the last n commits. 
    * log limit can be specified in other ways like: `--since`, `--before`, `--untill`, `--before`,
    `--author`, `--committer`, `--grep`
  * `--pretty` is probably the most useful argument - for example: `git log --pretty=oneline`
prints every commit in oneline.
  * --pretty lets to fully customize the output with `format`
  * There are more useful arguments for `git log`, I recommend reading about it <a href="https://git-scm.com/docs/pretty-formats"> here </a>

<h4> Undoing things </h4>

`git commit --amend` is extremely useful if you made a mistake with your last commit, e.g., wrote a wrong message
or forgot to add a file.

Unstage a file with `git reset HEAD <file>`

Unmodify a file with `git checkout -- <file>`

* Useful when you realised that changes you made since last commit are bad, and you should start again with last commit's state
* Be very careful with this command, because changes overwritten with `checkout` cannot be recovered, since they were never committed.

<h4> Managing remotes </h4>

It is needed while collaborating on any Git project. Working with other people
involve managing these remotes and pushing/pulling data to/from them. 

* `git remote` lists configured server, default one is origin. 
* `git remote add <name> <url>` add a new remote. It is usually also one of commands used while initializing a new repository.
* `git fetch <name>` fetches all the information from this remote.
* `git push <remote name> <branch name>` pushes your remote upstream.
  * If repository was cloned, git automatically assigns names of remote to `origin` and branch to `master`, although it is recommended to change default branch name to `main` with `git branch -M main` command. 
* `git remote show <remote-name>` displays information about a specified remote.
* `git remote rename <old name> <new name>` renames remote
* `git remote rm <remote name>` removes remote

<h4> Tagging </h4>

* `git tag`  lists available tags 
  * It also accepts specifying a pattern, e.g. `git tag -l 'v1.0*` lists all tags starting with v1.0
  
There are two main types of tags - lightweight and annotated. 
  * Lightweight tag is just like a pointer to a specific commit 
    * Those can be created simply with `git tag <name>`
  * Annotated tags are stored as full objects in git database
    * Those can be created with `git tag -a <name> -m <message>`
  * To tag already existing commit use `git tag -a <tag name> <commit id>`  

<h4> Personalize commands with aliases </h4>

It is possible to make your own names for specific commands.

* `git config --global alias.<name> <command>` sets an alias for specific command
    * Remember that command doesn't include "git" in front of it.
    * Example: `git config --global alias.comm commit` replaces 'git commit' command with 'git comm'

<h2 align="center"> Branching </h2>

#