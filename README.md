<h1 align="center"> Git notes based on book: "Pro Git" by Scott Chacon</h1>

---

<h3> List of content:</h3>
* Basics

---

<h4> Basics </h4>
Two approaches are: 

1. Take an existing project or directory and imports it into Git.
2. Clone an existing Git repository from another server

Initializing a repository in an existing directory: `git init`

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

 The lifecycle of status of files 

- Check the status with `git status` command
  * Use `-s` parameter to simplify output
    
Ignore files
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
  
View staged and unstaged changes
 * `git diff` compares what is in your working directory with what is in your staging area. 
* To show the difference between staged files and last commit use `git diff --staged`
    
