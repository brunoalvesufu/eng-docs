## 1- Configuring git:

```bash
git config --global user.name "user.name"
```

```bash
git config --global user.email "user.email"
```

The `--global` tag can be removed to associate a user to a specific repository.

## 2- Starting a local repository:

```bash
git init
```

A directory named `.git` will be added, that’s responsible for the version control.

## 3- Cloning an existing repository:

```bash
git clone repository-url
```

The local and the remote repositories are automatically linked with the commands above, there’s no need for using `git remote` anymore.

## 4- How does Git work:

There are three states in which the code can be while using git, those are MODIFY, STAGE, and COMMIT.

- **MODIFY** is the state of the files that are modified in comparison with the current version;
- **STAGE** is where the modified files ready to be added to the new version are put;
- **COMMIT** is the final stage, committed changes compose a new version.

Commits don’t erase the old files, versions in git work like a pointer that carries the modifications made. Check the status of the files with:

```bash
git status
```

Check the status of the files with a clean response with (usually for scripts):

```bash
git status --porcelain
```

## 5- Adding and committing:

To add a file to STAGE:

```bash
git add filename
```

To add all modified files at once:

```bash
git add -A
```

To add all modified files of a specific extension:

```bash
git add *.file-extension
```

A recently added file will appear as “Untracked” when you run the status command, it’s a type of MODIFY and it can be added with the add command or ignored if added to the `.gitignore` file inside the repository. The add command will stage the file.

To commit the staged files:

```bash
git commit -m "A descriptive message of this version (commit)."
```

To commit files in MODIFY, it stages and automatically commits the files:

```bash
git commit -a
```

Each commit has an immutable ID, the command above gives a description of the commits:

```bash
git log
```

To display the last N commits:

```bash
git log -N
```

To display a log of commits in branch-B but not in branch-A:

```bash
git log branch-A branch-B
```

To display a log of commits that changed a specific file:

```bash
git log --follow [filename]
```

To list changes between the current and the latest versions:

```bash
git diff
```

To list changes between the current and the latest versions for a specific file:

```bash
git diff filename
```

To display the differences between the local branch and a remote one:

```bash
git diff origin/remote-branch..local-branch
```

## 6- Undo changes:

Commits are immutable objects, a committed change can’t be changed. But it’s possible to make new commits that undo the changes or correct the incorrect information on previous commits.

Discards changes made to the file in MODIFY (irreversible action):

```bash
git checkout -- filename
```

Discards changes made to a file in STAGE (irreversible action):

```bash
git reset --hard HEAD
```

Discards the last commit made in the local repository (maybe irreversible action):

```bash
git reset --hard HEAD~1
```

If some work was lost with the command above, it can be reverted with:

```bash
git reflog
# this command shows the lost commit hash
git reset --hard lost-hash-number
# this command brings the commit back into the repository
```

To revert the changes of a specific commit:

```bash
git revert --no-commit commit-hash
```

## 7- Branches:

Branches work as if you created a new folder and copied the files to it, that doesn’t really happen but git makes it look like it. To create the branch:

```bash
git branch branch-name
```

To list the branches that already exist:

```bash
git branch
```

To switch to the branch just created:

```bash
git checkout branch-name
```

To create and automatically switch to it:

```bash
git checkout -b branch-name
```

To delete a branch:

```bash
git branch -d branch-name
```

To rename the current branch:

```bash
git branch -m new-branch-name
```

## 8- Merging Branches:

Once the modifications on the new branch are committed, it’s time to merge it with the “main” branch. So first switch to the branch that will receive the changes and run the following:

```bash
git merge branch-name
```

If a conflict appears, git will add markers to the file with the conflict. Use the `status` command to see which files are with conflict. Once they are solved, just try merging again.

## 9- Remote repositories:

The first thing to do is to configure the relationship between the local and remote repositories, and for that:

```bash
git remote add origin remote-repo-url
```

To check the `remote-repo-url` configured to your local repo, use:

```bash
git remote -v
```

Once it’s configured, just push the local repo to the remote one with:

```bash
git push -u origin main
```

To pull changes made to the remote repo, use:

```bash
git pull
```

The command above fetches and merges the changes. If you just want to bring the changes to your repo without merging them yet, use:

```bash
git fetch
```

## 10- Merge vs Rebase:

Merge is a type of commit, the changes added in another branch can be committed (merged) to another using the merge command; the merge itself is a new commit. Rebase is a reconstruction of the commit history, it brings the commits of a branch to another, as if they were done initially on the second branch. And yes, rebases are as dangerous as they seem to be.

The golden rule of rebasing is to never use it on public branches. If there’s anyone else working on the branch, don’t rebase it, conflicts and confusing galore shall appear.

## 11- Useful stuff:

Messed up the local main branch? If the remote main is the one you want back, try this:

```bash
git reset --hard origin/main
```

Watch out, the command above can be irreversible in some conditions.

Wanna add the files in “Untracked” to `.gitignore`? Use the following:

```bash
git status --porcelain | grep '^??' | sed 's/^?? //' >> .gitignore
```

The `??` is the identification provided by the `--porcelain` tag for the untracked files. You can play with it and add other files in different states to the command.

If you want to bring just a particular commit from another branch to yours, use the cherry-pick command:

```bash
git cherry-pick commit-hash
```

Adding the tag `-edit` to the command above will give you the option of editing the commit message before adding it to your branch.