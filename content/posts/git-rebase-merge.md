---
title: "Git Rebase Merge"
date: 2020-11-18T07:40:07+01:00
draft: true
---

References:
* [https://github.com/servo/servo/wiki/Beginner%27s-guide-to-rebasing-and-squashing](https://github.com/servo/servo/wiki/Beginner%27s-guide-to-rebasing-and-squashing)
* [https://www.digitalocean.com/community/tutorials/how-to-rebase-and-update-a-pull-request](https://www.digitalocean.com/community/tutorials/how-to-rebase-and-update-a-pull-request)
* [Delete a local or remote branch](https://makandracards.com/makandra/621-git-delete-a-branch-local-or-remote)

Let's start from an repo on gitHub, for example [Hugo Docs](https://github.com/gohugoio/hugoDocs)

First, let's fork it on GitHub on personal account

![Fork on GitHub](/img/fork-github.png)

Then `git clone` the forked repository. This would automatically create the associated repo as a _origin_ remote (visible with `git remote -v`)

Add the original repo as _upstream_ remote with `git remote add upstream git_repo_url`. This would allow to rebase before pushing.

Create a feature branch with `git checkout -b feature-branch` (-b puts you automatically on the newly created branch).

Work on the change, `git add` and `git commit`.

Once ready to make the Pull Request, time for rebase:
* First squash the commits to only have one (with `git rebase -i hash-of-commit-before-the-first-one-to-squash`)
* Then rebase from upstream: 
    * `git checkout master`
    * `git fetch upstream`
    * `git merge upstream/master`
    * `git checkout feature-branch`
    * `git rebase master`(his is also possible to ONLY rebase the feature branch but better to do it from _master_) 
* Finally, push our remote branch and do the Pull Request on GitHub
    * `git push origin feature-branch`
    * and create the PR

If we need to update the PR:
* Use the same approach than above (especially squash the commits) and at the end, "force push" to the remote branch with `git push -f origin feature-branch`