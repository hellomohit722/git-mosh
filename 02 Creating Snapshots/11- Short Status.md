# 11- Short Status

With the `git status` command we see the status of the **Staging Area** and **Working Directory**.

```zsh
❯ git status
On branch main
Your branch is ahead of 'origin/main' by 19 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   02 Creating Snapshots/11- Short Status.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md

no changes added to commit (use "git add" and/or "git commit -a")
```

We can pass the flag `-s` to `git status -s` to have a shorter version.

```zsh
❯ git status -s
 M "02 Creating Snapshots/11- Short Status.md"
?? "02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md"
```

In this output we have two columns,
The first column indicates the status of the index (staged changes), and the second column indicates the status of the working tree (unstaged changes).

We have modified file `02 Creating Snapshots/11- Short Status.md`, thats why we have a red **`M`** in the right column, but the left column is empty because we don not have staged this modifications.

File `02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md` is a new file, that why we have red **`?`** in both columns.

Now if we run `git add "02 Creating Snapshots/11- Short Status.md"`and add this file to the **Staging Area**, the output of `git status -s` will be:

```zsh
❯ gi status -s
M  "02 Creating Snapshots/11- Short Status.md"
?? "02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md"
```

Now The **`M`** is green and is in the left column, meaning the modifications are in the **Staging Area**.

If we keep modifying the file and run `git status -s` we will see to **`M`** one green and another red. And if we add the new file to the **Staging Area** we will see a green **`A`**.

```zsh
❯ git status -s
MM "02 Creating Snapshots/11- Short Status.md"
A  "02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md"
```


```
Symbol	Meaning  				Description
??		Untracked				New file that has not been added to the repository yet.
A		Added					File is added to the staging area (index).
M		Modified				File has been changed in the working directory but not staged.
M		Modified				File has been changed and the changes are staged.
MM		Modified				File is modified, staged, and then modified again (both columns).
D		Deleted					File is deleted and the deletion is staged.
D		Deleted					File is deleted in the working directory but not staged.
R		Renamed					File has been renamed in the staging area.
C		Copied					File has been copied in the staging area.
U		Updated but Unmerged	File has a merge conflict that needs to be resolved.
```

