# 02- What are Branches

Branches allows us to work in an isolated environment from the main line. So branches are a kind of separate isolated workspace.

![Branches line of work](./images/01-01.png "Branches line of work")

The principal line of work (branch) is called ***master*** or ***main***. When we need to work, for example, on a new feature we can create a new branch to work on that feature. And when we are done we merge the new feature branch into the ***main*** branch.

Git manages its history and branches not by copying files, but by creating and moving lightweight **pointers**.

---
# 🌳 How Git Manages Branches

When we create a new branch (e.g., `git branch new-feature`) Git creates a new pointer for that branch. When we work in that branch and make new commits Git moves that pointer forward, and the master pointer stays where it is.(This mechanism makes git so fast). This way Git knows the latest code in each branch. To know in which branch we are working on, Git uses the **HEAD** pointer, when we switch branchs `git switch <branch-name>` Git points the **HEAD** pointer to the branch we want to work on, and updates the **Working Directory** accordingly.

![Git branches](./images/01-02.png "Git branches")
