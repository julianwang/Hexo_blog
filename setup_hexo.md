title: "Setup Hexo Blog in VPS"
date: 2015-08-19 22:18:09
tags: Linux
---

# Setup Hexo Blog in VPS


### General：
There's many articles described how to setup Hexo Blog in VPS. 
The common steps usually looks like below.

>1. Install nodejs and hexo in local machine
2. Create bare git repository in VPS
3. hexo new post
2. Edit new post with local editor
3. hexo g -d to deploy to remote git repository
4. nginx/apache server provide http services with deployed static webs

It's quite straight forward and easy to go. But it's not the best option to me.
<!--- more --->

The **disadvantages** of traditional ways to me are
>1. I'm frequently switching between 2 desktops(at home/Windows7 and in office/Windows8.1) and 2 laptops(MacBookPro/OSX and Thinkpad/Ubuntu). It is not a good idea to install nodejs and hexo on all devices w/ various Operating system. 
2. My VPS has traffic quota. But traditional way will generate whole site and upload it again if you change something in common (e.g. theme or layout). This consums more traffic and also takes more time.
3. Most important thing is that, my client should keep light weight and clean. I don't want to install nodejs/hexo on it. git/markdown editor are ok because they are for daily use

So, here's my solution,
>1. Install nodejs and hexo in VPS
2. Create bare git repository in VPS
3. Use local editor create new post
4. Git push new post to VPS:/path/to/_posts/
5. Call git hook to execute hexo g
6. nginx/apache server provide http services with deployed static webs

Now you only need a local markdown editor, such as a chrome apps: stackeditor.
You create a post and execute git add/commit/push it to VPS bare repository.
Then it's done. 
>The only thing not good is that if you want to diagnostic something, you need try it on VPS side with hexo server.
