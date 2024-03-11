# Git

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
flowchart RL
    1((9ab80b0))
    main(main) -.-> 1
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
```

```bash
% touch test2.txt
% git add test2.txt
% git commit -m "added one more file"
[main(main) d2d0f24] added one more file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.txt
```

```mermaid
flowchart RL
    1((9ab80b0))
    2((d2d0f24))
    2 --> 1
    main(main) -.-> 2
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
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

Let's make one more change and add some text to `test.txt`:

```bash
% echo "here's a line of text" >> test.txt
% git add .
% git commit -m "added some text"
[main 370682a] added some text
 1 file changed, 1 insertion(+)
```

Our repository now looks like this:

```mermaid
flowchart RL
    1((9ab80b0))
    2((d2d0f24))
    3((370682a))
    2 --> 1
    3 --> 2
    main(main) -.-> 3
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 3 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
```

### Branching

We will now create a new branch so we can commit changes without affecting the main branch. Once we are ready, we can merge the changes back into the main branch.

A branch is really just a pointer to a commit. When we create a new branch, we create a pointer to the current commit.

We can use `git branch` and `git checkout` to create and switch branches, but there is a shortcut: `git checkout -b`.

```bash
% git checkout -b develop
Switched to a new branch 'develop'
```

```mermaid
flowchart RL
    1((9ab80b0))
    2((d2d0f24))
    3((370682a))
    2 --> 1
    3 --> 2
    main(main) -.-> 3
    develop(develop) -.-> 3
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 3 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style develop fill:#E1D5E7,stroke:#A680B8,stroke-width:1px
```

### Merging branches

## Using GitHub

### Creating a repository

### Cloning a repository

### Forking a repository

### Pull requests

### Issues
