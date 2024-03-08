# Git training

## What is git?

## What is GitHub?

## Using git

### Initializing a repository

```bash
% git init
Initialized empty Git repository in /Users/pieter/Desktop/git/.git/
```

```bash
% git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

### Adding files

Files can be added to the index using `git add`.

```bash
% git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	test.txt

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
% git add test.txt
```

```bash
% git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   test.txt
```

### Saving changes

Staged changes can be committed using `git commit`.

```bash
% git commit -m "first commit"
[main (root-commit) 9ab80b0] first commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.txt
```

```bash
% git status
On branch main
nothing to commit, working tree clean
```

```mermaid
gitGraph
    commit id: "9ab80b0"
```

```bash
% touch test2.txt
% git add test2.txt
% git commit -m "added one more file"
[main d2d0f24] added one more file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.txt
```

```mermaid
gitGraph
    commit id: "9ab80b0"
    commit id: "d2d0f24"
```

Check the commit history using `git log`.

```bash
% git log
commit d2d0f24cab33f87126e3d0108c13a8a3f86f8da3 (HEAD -> main)
Author: Pieter Provoost <pieterprovoost@gmail.com>
Date:   Fri Mar 8 20:05:12 2024 +0100

    added one more file

commit 9ab80b05e916d5a3065eae0a6603f06251fa8c28
Author: Pieter Provoost <pieterprovoost@gmail.com>
Date:   Fri Mar 8 19:15:05 2024 +0100

    first commit
```

### Branching

### Merging branches

## Using GitHub

### Creating a repository

### Cloning a repository

### Forking a repository

### Pull requests

### Issues
