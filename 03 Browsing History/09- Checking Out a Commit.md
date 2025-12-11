# 09- Checking Out a Commit

Historically used for switching branches/commits and restoring files.

## 🧭 Understanding Git Pointers:
 HEAD and BranchesAt its core, Git history is managed by special pointers.
 1. The Branch Pointer (main/master)A branch name (like main) is simply a pointer that always points to the latest commit in that sequence.When you create a new commit, Git creates the new commit object, and then the branch pointer (main) automatically moves forward to point to this new commit.
 2. The HEAD Pointer (Your Current Location)HEAD is Git's crucial pointer that tells it where you currently are in the repository.Normally, HEAD points to a branch name (e.g., HEAD $\rightarrow$ main). This means any new commits you create will automatically move both HEAD and the branch (main) forward.


When we need to see the complete project in a given point in time we can checkout a given commit, and it will restore our **Working Directory** to that point in time. Using the command `git checkout <commit>`. For example `git checkout 12156df`.

This will bring a warning:

```zsh
Note: switching to 'b9e25df'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at b9e25df start new lesson
```

## Detached HEAD state

In Git each commit is pointing to the last commit. That is how Git maintains history.

![Commit history](./images/09-01.png "Commit history")

Until all the commits created are part of a branch, the `master` or `main`. The way Git represents branches is using a pointer, so `master` is pointing to the last commit created. As we create new commits master moves forward to point to the last commit.

![Master branch](./images/09-02.png "Master branch")

Because we can have multiple branches Git needs to know in which branch we are working at the moment. To do that Git uses another special pointer called `HEAD`, so `HEAD` points to the current branch we are working on. In this case `master`. We have seen this in the `git log` command **`(HEAD -> main)`**.

```zsh
2ee3bb6 (HEAD -> main) add details to lesson
18869aa lesson complete
f2150f7 lesson complete
4acfee7 lesson complete
```

When we checkout a particular commit, the `HEAD` pointer will move to that commit, thats is what is called a `detached HEAD`. `HEAD` is not pointing to a branch but is pointing to a specific commit.

![detached HEAD state](./images/09-03.png "detached HEAD state")

In this situation we should not create new commits. If we make changes and create a new commit, that commit will be added where the `HEAD` pointer is at the moment. But eventual we will attach the HEAD pointer to a branch, so the commit created it is not reachable by any other commit or pointer, ist like a dead commit. Git checks for commits like these periodically and removes them to save space.

![detached HEAD state](./images/09-04.png "detached HEAD state")

Lost commit.

![lost commit](./images/09-05.png "detached HEAD state")

When you run git log --oneline without any extra flags, Git uses HEAD as the starting point for history traversal.

Behavior in Detached HEAD: When HEAD is pointing directly to an older commit (e.g., f2150f7), Git starts its log from there and works backward through the parent commits (4acfee7, dd6b4b2, etc.).

Result: It only shows commits reachable from HEAD. Since f2150f7 is an older commit, the newer commits that the main branch points to (ebbd4b1, 66cf5ab, 2ee3bb6) are not in the history path leading back from f2150f7. You cannot see the future commits.

The --all flag tells Git to start the log traversal from all references (branches, tags, and other pointers, including the main branch pointer).

Behavior in Detached HEAD: Git includes the entire history referenced by the main branch. It traces the history back from the tip of main (ebbd4b1) and the history back from HEAD (f2150f7) and combines them.

Result: It shows all reachable history in the repository. You see the complete commit graph, which clearly labels where main is pointing (the newest commit) and where HEAD is pointing (the older commit).

```zsh
ebbd4b1 (main) add details to lesson
66cf5ab add details to lesson
2ee3bb6 add details to lesson
18869aa lesson complete
f2150f7 (HEAD) lesson complete
4acfee7 lesson complete
dd6b4b2 fix: typo
b9e25df start new lesson
9f61863 style: change tab to spaces
[...]
```

To attache the `HEAD` pointer to the branch, use `git checkout <name of the branch>` in this case `git checkout main`.
