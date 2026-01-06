# Git & GitHub: Creating and Connecting Repositories

This guide covers the two main ways to start a project: starting from scratch locally or starting with an existing GitHub repository.

---

## Method 1: The "New Project" (Local First)
*Use this if you already have code on your computer and want to push it to a new GitHub repo.*

## 1. Initialize Local Repository
In your project folder, run:
```bash
git init
git add .
git commit -m "Initial commit"
```

## 2. Create the Repo on GitHub

Go to github.com/new.

Name your repository (do not initialize with a README/License if you have local code).

Click Create repository.

## 3. Link Local to Remote
Copy the URL of your new GitHub repo and run:
Add the remote link and name it 'origin'
`git remote add origin [https://github.com/USER_NAME/REPO_NAME.git](https://github.com/USER_NAME/REPO_NAME.git)`

Rename your local default branch to 'main' (if it's named 'master')
`git branch -M main`

Push your code and set 'origin/main' as the tracking reference
`git push -u origin main`

## Method 2: The "Clone" (GitHub First)
Use this if you created the repository on GitHub first (with a README or License) and want to bring it to your computer.

1. Copy the URL
On the GitHub repository page, click the green Code button and copy the HTTPS or SSH URL.

2. Clone to Local Machine
`git clone [https://github.com/USER_NAME/REPO_NAME.git](https://github.com/USER_NAME/REPO_NAME.git)`
Note: This automatically sets up the remote named origin and creates the origin/main tracking branch for you.
