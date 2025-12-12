# 07- Merging

[Git merging docs](https://git-scm.com/book/pt-br/v2/Git-Branching-Basic-Branching-and-Merging)

Merging is the process of integrating changes from a separate line of development (a branch) back into a primary branch. Git chooses one of two methods based on the history of the branches.

In Git we have two types of merges:

1. Fast-forward merges
2. 3-way mergers

## Fast-forward merges

When we create new brach, let's call it ***bugfix***, from the ***main*** branch, both branches, ***main*** and ***bugfix***, will be pointing to the same commit.

![New branch](./images/07-01.png "New branch")

Then when we switch to ***bugfix*** and start working on it and committing to it, the ***bugfix*** branch moves forward and **main** stays in the same place. This branches have not diverged and there is a direct linear path between them. It simply moves the `main` pointer forward to the commit where `bugfix` currently points.
 
* **Result:** The history remains a **single, linear line** of commits.

![Branches linear path](./images/07-02.png "Branches linear path")

This way all Git has to merge the changes to bring the master pointer forward. This is the fast-forward merge. Git run this type of merge when there is a direct linear path between the two branches.

![Branches linear path](./images/07-03.png "Branches linear path")

## 3-way merge

A 3-way merge happens when we apply some changes to the ***main*** branch, and commit them, after we created the ***bugfix*** branch. So we have some changes in ***main*** that do not exist in the ***bugfix*** branch. In this situation the two branches are diverged.

![Diverged branches](./images/07-04.png "Diverged branches")

Because `main` cannot simply be moved forward, Git must create a new commit to integrate the two separate lines of history. This commit is called a **Merge Commit**.

* **3-Way:** The merge commit is calculated based on three points:
    1.  The tip of the target branch (e.g., `main`).
    2.  The tip of the branch being merged (e.g., `bugfix`).
    3.  The **Common Ancestor** commit, which is the point where the histories diverged.
    
    Git uses the Common Ancestor as a baseline to figure out what was changed on *each* side, and then combines those changes.

![Merge commit](./images/07-05.png "Merge commit")

* **Result:** A **Merge Commit** is created, which has two parent commits, tying the two separate lines of development back together. This preserves the branch history on the commit graph.