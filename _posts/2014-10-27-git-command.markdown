---
layout: post
title:  "Git command I used most!"
date:   2014-10-27 08:16:42
categories: git
---

#### 简单的git代码提交流程
* 平时开发，在本地建一个'branch 你的姓名'，如'branch zhangsan'，并把开发代码提交到remote的'branch 你的姓名'。测试确认无问题后合入master
* 'branch master'作为产品更新的唯一branch
* 如果涉及到某个功能需要多人合作完成，这时把自己已经完成，并无不可运行错误的代码，从'branch 你的姓名'合入到'branch develop'中，等develop测试完毕，合入到master中

**可能涉及的一些git操作**
{% highlight bash %}
$ git reset --hard a_commit # 强行回滚到某个旧版本，这在很多时候都很好用，比如分支错乱git rebase又不会用的时候
$ git fetch # 如果git remote有更新，必须要fetch一下，否则可能找不到最新的commits
$ git cherry-pick a_commit # 把某个commit放到当前本地branch
{% endhighlight %}

#### git config
{% highlight bash %}
$ git config --global user.email 'mail_zlj a-t 163.com' ＃Set email
$ git config --global user.email #Show email
{% endhighlight %}

#### git remote
{% highlight bash %}
$ git remote add origin https://github.com/gazeldx/duokong.git #Add a remote URL
$ git remote -v #List all remotes
$ git remote set-url origin https://github.com/gazeldx/hutch.git
$ git remote add upstream https://github.com/gocardless/hutch.git
$ git ls-remote # list remote branches
{% endhighlight %}

#### git push
{% highlight bash %}
$ git push -u coding coding_local:master # Push to (coding master) remote branch from coding_local branch
{% endhighlight %}

#### git branch
{% highlight bash %}
$ git branch # View local branches
$ git branch -r # View remote branches
$ git branch -d the_local_branch # Delete a local branch
$ git push origin --delete develop # Delete a remote branch develop.
如何在remote上创建一个branch？下面两句即是，参考自：http://stackoverflow.com/questions/1519006/how-do-you-create-a-remote-git-branch
$ git checkout -b your_branch # 这句话不会修改任何代码。git pull才会。your_branch的内容是独立的。如果是新建的，则等于现在的内容。
$ git push <remote-name> <branch-name> # E.g: git push origin your_branch
{% endhighlight %}

{% highlight bash %}
如何合入到master？下面几句即是，参考自：http://stackoverflow.com/questions/5601931/best-and-safest-way-to-merge-a-git-branch-into-master
$ git checkout master
$ git pull origin master
$ git merge test
$ git push origin master
$ git log <path/branch>
{% endhighlight %}

#### git stash
{% highlight bash %}
$ 可以把一些改动先藏起来。这样就可以成功pull 代码了，否则可能报错有冲突，不让你pull。pull完代码后，再git stash apply stash@{id}，就可以把本地藏起来的改动合入本地，可能需要你解决一下冲突。
$ git stash list
$ git stash show -p stash@{0} # 查看stash@{0}内容
$ git stash apply stash@{0} # 将stash@{0}内容恢复到当前版本
{% endhighlight %}

#### pull request
{% highlight bash %}
https://help.github.com/articles/checking-out-pull-requests-locally/
https://help.github.com/articles/merging-a-pull-request/
$ git pull git://github.com/chenge/ruby-db-admin.git master # Merge from Pull request
{% endhighlight %}