# Git

## What is git?

## Initializing a repository

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

## Adding files

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

## Saving changes

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

## Branching

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

If we now make more changes and commit them, the `develop` branch will move forward, but the `main` branch will stay where it is.

```bash
% echo "here's a line of text" >> test2.txt
% git add .
% git commit -m "added text to test2.txt"
[develop aac8ffc] added text to test2.txt
 1 file changed, 1 insertion(+)
```

Now switch back to the `main` branch and make a change there.

```bash
% git checkout main
Switched to branch 'main'
% echo "here's another line of text" >> test.txt
% git add .
% git commit -m "changed the first file"
[main 5d5cf50] changed the first file
 1 file changed, 1 insertion(+)
```

```mermaid
flowchart RL
    1((9ab80b0))
    2((d2d0f24))
    3((370682a))
    4((aac8ffc))
    5((5d5cf50))
    2 --> 1
    3 --> 2
    4 --> 3
    5 --> 3
    main(main) -.-> 5
    develop(develop) -.-> 4
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 3 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 4 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 5 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style develop fill:#E1D5E7,stroke:#A680B8,stroke-width:1px
```

## Merging branches

`git merge` incorporates changes from another history into the current branch. The result is recorded in a new commit.

```bash
% git merge -m "merge branch develop" develop
% git merge develop
Merge made by the 'ort' strategy.
 test2.txt | 1 +
 1 file changed, 1 insertion(+)
% git log
commit 3d4cdcae41f1ff8ab7811db0a700fbc4876164ec (HEAD -> main)
Merge: 5d5cf50 aac8ffc
Author: Pieter Provoost <pieterprovoost@gmail.com>
Date:   Wed Mar 13 14:53:57 2024 +0100

    merge branch develop
```

```mermaid
flowchart RL
    1((9ab80b0))
    2((d2d0f24))
    3((370682a))
    4((aac8ffc))
    5((5d5cf50))
    6((0fa2c35))
    2 --> 1
    3 --> 2
    4 --> 3
    5 --> 3
    6 --> 5
    6 --> 4
    main(main) -.-> 6
    develop(develop) -.-> 4
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 3 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 4 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 5 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 6 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style develop fill:#E1D5E7,stroke:#A680B8,stroke-width:1px
```

## Working with remotes

```bash
% git remote add origin https://remote-repo-url.git
```

```bash
% git push --set-upstream origin main
Enumerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 10 threads
Compressing objects: 100% (12/12), done.
Writing objects: 100% (15/15), 1.36 KiB | 1.36 MiB/s, done.
Total 15 (delta 1), reused 0 (delta 0), pack-reused 0
To https://remote-repo-url.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

```bash
% git push --set-upstream origin develop
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://remote-repo-url.git
 * [new branch]      develop -> develop
branch 'develop' set up to track 'origin/develop'.
```

```mermaid
flowchart TB
    subgraph local
    direction RL
    1((9ab80b0))
    2((d2d0f24))
    3((370682a))
    4((aac8ffc))
    5((5d5cf50))
    6((0fa2c35))
    2 --> 1
    3 --> 2
    4 --> 3
    5 --> 3
    6 --> 5
    6 --> 4
    main(main) -.-> 6
    develop(develop) -.-> 4
    style 1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 3 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 4 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 5 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style 6 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style main fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style develop fill:#E1D5E7,stroke:#A680B8,stroke-width:1px
    end
    subgraph remote ["remote (origin)"]
    direction RL
    r1((9ab80b0))
    r2((d2d0f24))
    r3((370682a))
    r4((aac8ffc))
    r5((5d5cf50))
    r6((0fa2c35))
    r2 --> r1
    r3 --> r2
    r4 --> r3
    r5 --> r3
    r6 --> r5
    r6 --> r4
    rmain(main) -.-> r6
    rdevelop(develop) -.-> r4
    style r1 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style r2 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style r3 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style r4 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style r5 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style r6 fill:#D5E8D4,stroke:#67AB9F,stroke-width:1px
    style rmain fill:#F8CECC,stroke:#EA6B66,stroke-width:1px
    style rdevelop fill:#E1D5E7,stroke:#A680B8,stroke-width:1px
    end
    local -- push --> remote
    remote -- clone<br/>pull (fetch + merge) --> local
```
