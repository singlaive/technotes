---
layout: post
title: "Git pages in 2hours"
description: "This is an ariticle about tutorial to git pages."
category: Tutorial
tags: [Github, Github pages, Jekyll]
---
{% include JB/setup %}

###Why do I build my blog on Git pages?
Ah, because Github does not charge me a penny for its highly reliable service, and no ads, full stop. If you ever tried to find out a free or cheap hosting service provider, you will definitely know what I mean.

Secondly, it feels geeky. I am not a nerd (believe you are not either), but geek is not bad.

###Why do I use Jekyll? Hang on, what is it? What is the funny 'll' from?
You don't have to, really. You can just create some html (like index.html etc.) and Github will manage it pretty well. But Jekyll is the official tool Github uses to parse your articles. And it is hassel so free, so why not.

Truely no idea why jekyll is spelled like this, not by me. [Jekyll](http://jekyllrb.com/docs/home/) is a text transformation engine. Not a sensible wording for you? Fine, it builds blog for you, as an alternate tool of [Word Press](https://wordpress.org/).

 - It is simple (quite light wight) to use. Like what it says, "make it work in 3sec"
 - Your blog it builds responses extremely fast. Coz it renders static files only, no JS, nothing to slow it down.
 - Free to use, supporting all popular platform *unix, Mac, Windows (not officially though) etc.

###How long I need to build up an awesome look website/bog, 2hours?

Depending on how you want to play with it. If you just follow the instructions below blindly not bothering knowing details, probably after 10min you will have your site running (see how easy it is!). But if you want to know what you installed, why you type commands like that, and how you can customise the site for yourself, you need a bit more effort.

This tutorial expects you

 - Have both hands (or one finger...) which can type Linux commands.
 - Knows a little bit about git, like `git add` or `git commit`. That is almost sufficient! :) If serieouly you don't know much, no worry, I will explain to  you.
 - Heard about the funny words like Markdown, HTML, Ruby, etc. You don't really need to be expert about them.

Here we go.

Hang on, have you got a login on github yet? No? [Do it now](https://github.com/)! It might cost you 3min. 

Now you need create a new repository for your website or blog. There are two types of repositories you will need to think of: user page or project page. They differ in use cases and you are free to create either of them. You can delete and try again your repositories as many times as you like. So don't be shy and try it out.

 - A user can only create one user page. It can be considered hold the content about the user himself.
 - A project page, literally, is focused on one project you run. For example, you might want to maintain two blogs, one for business, and one for personaly life. You don't want to mix them up, do you? There are no limit of amount of project pages you can create.

There are other differences that I will cover later. The most difference between the two is the repository name. A project page name can be anything meaningful, like "greate_ideas_from_a_genius". But a user page name can only be in the patten of "username.github.io", replacing *username* with your own username. Now you see how come you can only have one user page! You are absolutely correct, there is no such a drop-down manu when you create a repository about which type of page to create. It comes up with the repository name. For snapshots and more details about repository creating, you can take a look at [this](http://www.thinkful.com/learn/a-guide-to-using-github-pages/). 

Now I assume you have a valid github account and a repository ready (say, in the name of my-awesome-site). We are going to build your blog locally, prettify it, and deploy it. Here I give all commands you need to type for your first go from scrach. I will tell you why doing so line by line. All commands have been verified working under Ubuntu  14.04 LTS.

	//Install Jekyll	
	sudo apt-get install ruby-dev
	sudo apt-get install nodejs
	sudo gem install jekyll
	//Build your site using JekyllBootstrap
	git clone https://github.com/plusjade/jekyll-bootstrap.git my-awesome-site
	cd my-awesome-site
	rake theme:install git="git://github.com/jekyllbootstrap/theme-mark-reid.git"
	jekyll serve
	//Install git
	sudo apt-get install git
	//Put everything under source control and upload them to Github
	git init
	git remote add origin https://github.com/username/my-awesome-site.git
	git checkout --orphan gh-pages
	git add *
	git commit -m "Initial commit"
	git push origin gh-pages

###Jekyll Installtion
I won't tell y ou for the first time how long it took me to install Jelyll locally. It is definitely longer than most of the tutorial tells you! After bunch of weird failurs and googling and excercising, the commands I show you here should let you run Jekyll pain-free in 2min. Again, I am talking about Ubuntu, 1404. Things might be different in other OS and versions.

	sudo apt-get install ruby-dev

You must have Ruby enviroment in your machine. If you are Rubyer, you might got it already. This command gave you everything Jelly needs. Why Ruby? Because Jelyll is written by Ruby. Some tutorials (even in Jekyll official site) might suggest you do apt-get install ruby, and/or apt-get install gem. That's not enough and you might end up with error "Failed to build gem native extension." This line equals to sudo apt-get install ruby-1.9.1-dev now. But I guess once Ruby updates itself, ruby-dev should still work but ruby-1.9.1-deb might not be.

	sudo apt-get install nodejs
Running Jelyll needs Javascript runtime engine. (Don't ask me what that means, I don't know and you don't have to know either.) NodeJs is one choice. And it always works. Just for info, NodeJs is a framework on top of Javascrip that allow Javascript run on server. Javascript normally is used at client side as the building block of the current WWW world. 

	sudo gem install jekyll
Gem is the package manager in Ruby, analog to apt-get for Ubuntu. Doing so you have Jekyll installed locally.
	
	sudo apt-get install git
Now we have git installed in you machine if you havn't done so yet. Currently you have nothing in your local folder. You have the option that builds a static html blog manually, and upload it to your repository. But we are not going to do that because we will use Jekyll to relief the pain of maintaining a website. Therefore instead of creating a website from scrach, we do
	git clone https://github.com/plusjade/jekyll-bootstrap.git my-awesome-site
This command creates a subfolder of name my-awesome-site (can be anything) under your current folder, and download the source code of Jekyll-Bootstrap into this subfolder. Hang on, did I mention Jekyll-Bootstrap before? No? Well, some smart guy added a bunch of features and several nice looking thames based on Jekyll. I choosed it since I am very lazy to build up my own UI for the blog. I will show you how to do a bit customization afterwards. If you just want to try Jekyll itself, you need to replece the git link as:
	jekyll new my-awesome-site
Similarly, this Jekyll command create a subfolder, and copy al necessary files (whici is a subset of what we have above) into it. 
Of course, now it is time to take a close look at how the website look like that Jekyll builds for you! We do:

	cd my-awesome-site
	jekyll serve
Now open one of your web browser, Chromium or Firefox etc., type in the address bar:
	http://0.0.0.0:4000
Hey not bad isn't it? If you like the current look you can start writing your new posts now. Buf if you want try something different, you can check [here](http://themes.jekyllbootstrap.com/). To apply different theme, for instance, you can change to mark-reid theme in this way:
	rake theme:install git="git://github.com/jekyllbootstrap/theme-mark-reid.git"
If you have not seen rake commande before, it is a Ruby utility analog to make command in general *unix world. You can find out a local file (my-awesome-site/Rakefile) provided along with Jekyll-bootstrap which downloads the theme files and adopts it for you in your site. Now you can try again see the new look. Oh, I am afraid you might need to type Ctrl+c firstly to interrupt Jekyll server process, then type `jekyll serve` again. Refresh your browser, like it?
Suppose you do, well if not, repeat the above steps till you find out the one you do like. Now you have your lovely blog built and run locally. Next you do want to see it on internet I believe. Very simple, do (surely ctrl+c first, or open a new terminal window and go to your site folder):

//Remove .git and reninit your own one!!!
	git remote add origin https://github.com/username/my-awesome-site.git
This lovely command link you local git repository to your remote one. It adds the remote repository and gives it a name origin. You can give it any meaningful name. Currently your local git repository 

	git checkout --orphan gh-pages



























[Automatic generatoer](https://help.github.com/articles/creating-pages-with-the-automatic-generator/)

























