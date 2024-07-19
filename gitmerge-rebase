# An Introduction to Git Merge and Git Rebase

![learn-git/images/image-3.png](images/image-3.png)

Git Merge and Git Rebase serve the same purpose. They are designed to integrate changes from multiple branches into one. Although the final goal is the same, those two methods achieve it in different ways.

### Git Merge

![learn-git/images/image-1.png](images/image-1.png)

In Git, `git merge` is a command that combines the changes from one branch into another branch. It creates a new commit, often referred to as a **"merge commit**," that has two parent commits, preserving the history of both branches. This is a common way to integrate changes from one branch, such as a feature branch, into another branch, typically the main or master branch.

#### Here’s how to use git merge:

* **Switch to the Target Branch:** First, you need to be on the branch where you want to merge the changes. For example, if you want to merge changes from a feature branch into the main branch, switch to the main branch:

```
git checkout main
```
* **Merge the Source Branch:** Then, use the `git merge` command to merge the changes from the source branch, for example: the feature-branch, into the target branch “main” in this case:

```
git merge feature-branch
```

* **Resolve Conflicts (if any):** Git will attempt to automatically merge the changes, but if there are conflicting changes in both branches, you’ll need to resolve these conflicts manually.

* **Complete the Merge:** Once conflicts (if any) are resolved, and you’re satisfied with the merge, you can commit the changes to create the merge commit.

#### When to Use Git Merge:

Use `git merge` in the following scenarios:

1. Shared Branches: When you’re working on a project collaboratively and want to integrate changes from feature branches into the main branch.
2. Public Repositories: In open-source projects, using merge commits can provide a clear history of contributions.

To summarize, `git merge` is a Git command that is used to integrate changes from one branch into another. It creates merge commits to preserve the history of both branches, making it suitable for shared or public repositories and collaborative development.

### What is Git Rebase?

![!\[alt text\](image-2.png](images/image-2.png)

In Git, `git rebase` is a powerful command that allows you to change the base of your current branch. Essentially, it rewrites the commit history of your branch by moving it to a new starting point, usually another branch.

To put it simply, when you perform a rebase, Git takes the commits from your current branch and reapplies them on top of the target branch. This creates a linear, more organized commit history by eliminating the merge commits that can clutter your project’s history.

#### How to Use Git Rebase:

* **Switch to Your Branch:** First, make sure you’re on the branch you want to rebase. For example, if you’re on a feature branch and you want to rebase it onto the “main” branch:

```
git checkout feature-branch
```

* **Initiate the Rebase:** Use the `git rebase` command followed by the name of the branch you want to rebase onto. For example, to rebase your “feature-branch” onto “main”:

```
git rebase main
```

* **Resolve Conflicts (if any):** During the rebase, Git might encounter conflicts when applying your commits on top of the new base. You’ll need to resolve these conflicts manually. Read this article on how to resolve conflicts.
* **Complete the Rebase:** Once you’ve resolved any conflicts, continue the rebase with:

```
git rebase --continue
```

* **Finish the Rebase:** When the rebase is complete, you’ll have a linear history with your branch’s changes neatly applied on top of the target branch.

#### When to Use Git Rebase:

Use **git rebase** in the following scenarios:

1. Feature Branches: When you’re working on a feature or topic branch and want to keep your commit history clean before merging into the main branch.
2. Keeping a Linear History: To maintain a clear and linear project history, especially in open-source projects or team collaborations.

`git rebase` is a valuable Git command that helps you create a more organized and linear commit history by moving your branch's changes to a new base. It's a powerful tool for keeping your project history clean and comprehensible.

### Advantages

#### Git Merge:

* **Preserves History:** It clearly shows when and where a branch was merged into another branch, making the history more explicit.
* **Simple Workflow:** It’s straightforward and works well for shared or public branches where others need to see the history.

#### Git Rebase:

* **Linear History:** It creates a clean, linear history without the clutter of merge commits, making it easier to follow the project’s progression.
* **Interactive Rebase:** You can reorder, edit, or squash commits during the rebase, allowing for a more organized and cleaner history.
Easier Conflict Resolution: Conflicts are often easier to manage during a rebase since you address them one by one as you apply the changes.

### Key Differences
* **History:** Merge creates merge commits, preserving the branch’s history, while rebase creates a linear history.
* **Commit IDs:** Merge retains original commit IDs, while rebase assigns new commit IDs.
* **When to Use:** Merge is suitable for shared branches or when you want to maintain a clear branching history. Rebase is great for feature branches, ensuring a clean and organized commit history.


# What's the difference between `merge` and `rebase`?

Reading the official Git manual it states that **“rebase reapplies commits on top of another base branch”**, whereas **“merge joins two or more development histories together”**. In other words, the key difference between `merge` and `rebase` is that while `merge` preserves history as it happened, `rebase` rewrites it.

Let's contextualize these statements with a side-by-side example!

![C:\devops\daws-78s\repos\learn-git\images\image.png](images/image.png)

As illustrated above, the `merge` operation intertwined the branches together by creating a new single merge commit **(C7)**, causing a diamond shaped non-linear history — essentially preserving history as it happened. By comparing this result with the outcome from the `rebase` action we see that no merge commit was created, instead the two commits **C5** and **C6** simply got rewinded and reapplied straight on top of **C4**, keeping the history linear.

If we scrutinise the two reapplied commits even further, we can see that the hashes have changed, indicating that `rebase` truly rewrites history. 

### Worth noting
Whenever you `rebase` a branch, new commits will always be generated even though the content might still be the same! That said, any former commits will eventually (post garbage collection) be deleted from history if no other pointer (branch/tag) is referencing them.

### With great power comes great responsibility
We’ve seen how rebase rewrites history, while merge preserves it. But what does this mean in a broader sense? And what possibilities and potential drawbacks do the two operations come with?

### Conflicting changes
Let’s say, for example, you’ve had some nasty conflicts trying to integrate the changes. In the merge scenario, you would have only needed to solve the conflicts once, straight in the **C7** commit. With rebase, on the other hand, you could potentially have been forced to solve similar conflicts in each commit **(C5 and C6)** as they were reapplied.

### Published branches
Another potential problem related to rebase occurs when the branch you are rebasing has already been published remotely, and someone else has based their work on it. Then, your rebased branch can cause serious confusion and headaches for all involved parties as Git will tell you that your branch is both ahead and behind at the same time. If this happens, pulling remote changes using the rebase flag (`git pull --rebase`) generally solves the problem.

Furthermore, whenever you are rebasing an already published branch, regardless if no one else has based their work on it, you’ll still need to force push it to get your updates to the remote server — overwriting the existing remote reference completely.

### Loss of data (to your advantage)
intially, as rebase rewrites history while merge preserves it, it’s possible to actually lose data when rebasing. When new commits are reapplied, the old ones are (eventually, post garbage collection) deleted. This same trait is in fact what makes rebase so powerful — it allows you to tidy up your development history before making it publicly available!

### Conclusion
While `merge` is safe to use from a potential data loss perspective, and can feel more straight forward to use. Here are some pointers that can help you avoid the most common issues related to `rebase`.

* Don't rebase a branch that’s been published remotely…

* …unless you know you are the only one working on it (and feel safe force pushing)

* Prior to rebasing, create a backup branch from the tip of the branch you’re about to rebase, as it will allow you to easily compare the outcome (once done) and jump back to the pre-rebase state if necessary.

**Source:** Above excerpt is taken from this full length post on the subject: https://blog.git-init.com/differences-between-git-merge-and-rebase-and-why-you-should-care/

