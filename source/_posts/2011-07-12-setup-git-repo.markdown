---
comments: false
date: 2011-07-12 20:48:22
layout: post
slug: setup-git-repo
title: SETUP GIT REPO
wordpress_id: 526
categories:
- git
---

#### ADDING KEY TO SERVER



`scp ~/.ssh/id_rsa.pub git@myserver.com:~/.ssh/authorized_keys`



#### SERVER


`sudo mkdir /home/git/myrepo
cd /home/git/myrepo
sudo git --bare init
sudo chown -R git:git /home/git/myrepo
`



#### CLIENT


`mkdir myrepo
cd myrepo
git init

# add some files

git add .
git commit -m "added some files"

git remote add origin git@myserver.com:myrepo
git push origin master

rm -r myrepo/
git clone git@yourserver.com:myrepo
`
