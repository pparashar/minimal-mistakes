---
id: 754
title: 'git Primer : Quick Reference Guide'
date: 2014-05-28T02:00:54+00:00
permalink: /git-primer-quick-reference-guide-2014-05.html
pvc_views:
  - "8812"
dsq_thread_id:
  - "2717091343"
categories:
  - Technology Insider
  - 'Tips, Tricks &amp; Hacks'
tags:
  - git
  - Tools
---
### All Important Book:

<a title="Git Book" href="http://git-scm.com/book/en/" target="_blank">http://git-scm.com/book/en/</a>

### Install Latest Version

    sudo add-apt-repository ppa:git-core/ppa
    sudo apt-get update
    sudo apt-get install git

### Intial Configuration

<p style="padding-left: 30px">
  git config &#8211;global user.name &#8220;Prashant Parashar&#8221;<br /> git config &#8211;global user.email &#8220;email@myemailwhatever.com&#8221;<br /> git config &#8211;global core.editor vim
</p>

<p style="padding-left: 30px">
  <strong>To use https URL of repository and cache password:<br /> </strong>git config &#8211;global credential.helper cache<br /> git config &#8211;global credential.helper &#8216;cache &#8211;timeout=86400&#8217;
</p>

### Clone a Repository

<p style="padding-left: 30px">
  cd Directory_where_need_setup<br /> git clone Repo_URL
</p>

### Basic Operations

  * **git pull** origin branch_name : pull from remote & merge into local
  * **git push** origin branch_name : push local committed changes to remote. **pull must precede the push**.
  * **git branch** branch_name : creates a new branch. does not change the working branch. <span style="text-decoration: underline">Must be followed</span> by &#8220;git checkout&#8221;
  * **git branch &#8211;set-upstream-to**=origin/REMOTE\_branch Local\_branch_name :  sets remote-local association for the branch(tracking branch) so that you can simply do &#8220;git pull&#8221; or &#8220;git push&#8221; while working in a branch.
  * **git checkout** branchname : sets the branch as working branch in current directory. Entire code switches to &#8220;the&#8221; branch
  * **git add** filepath: to add a new/modified file to stage it in repository before commiting
  * **git commit** -m &#8220;commit message&#8221; : commits all the staged changes to repository
  * **git commit -a** -m &#8220;commit message&#8221; : adds and commits files. to avoid git add and git commit
  * **git status** : shows what needs to be added to staging and what needs to be committed.
  * **git diff** : shows actual differences with staged/committed repository
  * **git diff &#8211;staged** : shows what you have staged (using git add) which would get committed if you run &#8220;git commit&#8221;
  * **git rm** filename\_or\_path : removes a file from git. Remove from local tree first.
  * **git rm &#8211;cached** filepath : removes the files from git staging area but keep in your local tree. Useful in removing files you forgot to add to .gitignore
  * **git log** : shows the commit history
  * **git log -5** : shows last 5 commit logs
  * **git log -p** -5 : shows differences as well
  * **git log -10 &#8211;pretty=format:&#8221;%h &#8211; %an, cr : %s&#8221;**  **&#8211;graph** : good way of printing pretty log
  * **git commit &#8211;amend** : commits the changes to the previous commit. In case you forgot some changes to earlier commit
  * **git checkout &#8212; filename** : destros local changes to file and get it from repository

### Tags

<p style="padding-left: 30px">
  <strong>git tag</strong> : shows all tags<br /> <strong>git tag -a TagName -m</strong> &#8220;Tag message&#8221;  : Adds an annotated tag<br /> <strong>git tag -a Tag -m</strong> &#8220;message&#8221; <strong><em>commithash</em></strong> : tag later using hash of commit<br /> <strong>git push origin &#8211;tags</strong> : push all tags to origin. By default not tags pushed.
</p>

### Working with Branches & Merges

Merge a branch with trunk/QA branch:

<p style="padding-left: 30px">
  git checkout main_branch_name<br /> git merge branch_to_merge_with_main_branch
</p>

<p style="padding-left: 30px">
  <strong>git branch -d branchname</strong> : deletes a branch
</p>

<p style="padding-left: 30px">
  <strong>git branch &#8211;merged</strong> : shows branches that have already been merged to another branch.
</p>

### Stashing Changes

Before switching branches, make sure using &#8220;git status&#8221; that the working directory is clean. If not, commit or stash the changes first.

<p style="padding-left: 30px">
  <strong>git stash</strong> : pushes the current changes to stash stack<br /> <strong>git stash list</strong> : lists the stashes<br /> <strong>git stash apply</strong> : pulls the stash from top of stack. stash remains on the stash until &#8220;git stash drop&#8221; is run<br /> <strong>git stash drop</strong> : drops the to item off stash<br /> <strong>git stash apply</strong> Stash_Name : applies particular stash<br /> <strong>git stash drop</strong> Stash_name : drops particular stash<br /> <strong>git stash branch</strong> branchname : creates a new branch out of stash
</p>

### Removing a file from every commit

git filter-branch &#8211;tree-filter &#8216;rm -f filename.txt&#8217; HEAD

&nbsp;
