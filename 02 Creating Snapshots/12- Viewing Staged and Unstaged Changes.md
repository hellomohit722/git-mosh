# 12- Viewing Staged and Unstaged Changes

Before committing code it is a best practice to review your code. To do that we can use the `git diff` command.

## Comparing between **working directory** and **Staging Area**
>  if staging area is empty/clean, there is no difference to show.

````
+## git diff command

+Before committing code it is a best practice to review your code. To do that we can use the `git diff` command.
+
+```zsh
+git diff --staged
+```
\ No newline at end of file
````



## Comparing between **Staging Area** and **last commit**
git diff --staged => This show what you have staged but haven't committed.

````zsh
❯ git diff --staged
diff --git a/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md b/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md
index 561ffc0..3661360 100644
--- a/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md
+++ b/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md
@@ -1,3 +1,9 @@
 # 12- Viewing Staged and Unstaged Changes
````

In the first line we can see that the `diff` utility as called and with which arguments, what files we are comparing. The **`a/...`** is what we have in the last commit and **`b/...`** is what we currently have in the **Staging Area**.

```zsh
diff --git a/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md b/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md
```

After that we have a legend, changes in the old copy are marked with a red **`-`**, and changes to the new copy are marked with green **`+`**.

```zsh
--- a/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md
+++ b/02 Creating Snapshots/12- Viewing Staged and Unstaged Changes.md
```

The legend is followed by a header, that tells us what parts of our file have been changed. The changes are split in chunks and there is a header for each chunk.

The **`-1,3`** referes to the old copy. It means starting from line one **`1`** three **`3`** lines have been extracted and shown here.

The **`+1,5`** referes to the new copy. It means starting from line one **`1`** five **`5`** lines have been extracted and shown here.

```zsh
@@ -1,3 +1,9 @@
```

## git diff HEAD 
> difference between working directory and last commit (skips staging area, shows everything)

| Repository State                               | `git diff` Output               | `git diff --staged` (or `--cached`) Output |
| ---------------------------------------------- | ------------------------------- | ------------------------------------------ |
| Nothing staged, nothing committed (empty repo) | Empty                           | Empty                                      |
| Changes made but **not staged**                | Shows changes                   | Empty                                      |
| Changes **staged**                             | Empty                           | Shows changes                              |
| Both staged and unstaged changes               | Shows **unstaged** changes only | Shows **staged** changes only              |
