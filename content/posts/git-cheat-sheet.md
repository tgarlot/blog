---
title: "Git Cheat Sheet"
date: 2020-11-19T08:08:53+01:00
draft: false
description: "Git commands to know"
tags: ["Development","Git"]
---

# Delete branch

Local branch: `git branch -d the_local_branch`

Remote branch: `git push origin :the_remote_branch` or `git push origin --delete the_remote_branch`

# Reset to Upstream

```bash
# ensures current branch is master
git checkout master

# pulls all new commits made to upstream/master
git pull upstream master

# this will delete all your local changes to master
git reset --hard upstream/master

# take care, this will delete all your changes on your forked master
git push origin master --force
```