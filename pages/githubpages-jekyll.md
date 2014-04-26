---
layout: page
title: Setting up GitHub Pages with Jekyll
description: 
---
{% include JB/setup %}


Outside of using the [automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator) provided by GitHub or writing your own .html files, there are several ways to set up your repository either for a `user page` or `project page` with the initial set of files needed to create a website.  Both of the following ways use `jekyll` to create beautiful website written in Markdown (.md) files.  

1. Use Jekyll directly. 

2. Clone a repository which contains all the jekyll files needed to create a website such as the [jekyll-bootstrap repository](https://github.com/plusjade/jekyll-bootstrap) or [Karl Broman's simple_site repository](https://github.com/kbroman/simple_site).


## Jekyll
To get started, I encourage you to follow the instructions on the [GitHub Help: Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages) website. 

#### Installing Jekyll
The installation of Jekyll depends on [Ruby](https://www.ruby-lang.org/en/) and [Bundler](http://bundler.io).  To install Bundler, run the command

	$ gem install bundler
	
To install Jekyll, run the command

	$ gem install jekyll

#### Using Jekyll	
The basic jekyll command to create a basic jekyll directory called `myrepo` is `jekyll new`: 

	$ jekyll new myrepo
	$ cd myrepo
	$ git init

If the repo is empty there will be no error messages. If the repo is not empty, it will complain about there being files already in the repo.  Just move the files to a different places temporarily and rerun the command. A new set of files should appear in the directory.  Copy all of the files you moved back into the repo and run this command in the `myrepo` directory: 

	$ jekyll build
	$ jekyll serve
	
To view the website locally, go to [http://localhost:4000](http://localhost:4000). Afterwards you can press ctrl-c to stop the process in the terminal.  You can also add the `--watch` command at the end to force Jekyll to rebuild the site every time you save the file. 

	$ jekyll serve --watch
	
Create and edit the Markdown files for your website, then commit your changes. 

	$ git add .
	$ git commit -m "initial page commit"

This is a very basic website, but you can edit the Markdown files to personalize it.  If this is repository is meant to be your User Page, you can use the `master` branch to publish your website.  If this is Project Page, change the name of the `master` branch to `gh-pages` and push to GitHub: 

	$ git branch -m master gh-pages 
	$ git remote add origin git@github.com:username/myrepo.git
	$ git push -u origin gh-pages


## Jekyll-Bootstrap
[Jekyll-Bootstrap](http://jekyllbootstrap.com) is similar to using `jekyll`, but it takes away a lot of the hassle about Jekyll by allowing the user to create blog-aware websites using markdown with [themes](http://themes.jekyllbootstrap.com). 

#### Getting started with Jekyll-Bootstrap
Here I will create a `project page` called `myrepo` using Jekyll-Bootstrap. First, use `git clone` to get a copy of the jekyll-bootstrap repository on Github and change the name of the directory from jekyll-boostrap to your repository's name (e.g. `myrepo`). You must remove the .git directory because you don't want the history of that repository as it will become your website.  Finally, make the directory a new git repository with `git init`. 

	$ git clone https://github.com/plusjade/jekyll-bootstrap
	$ mv jekyll-bootstrap myrepo
	$ cd myrepo
	$ rm -rf .git
	$ git init 
		
To quickly view the website as it is locally as it is, run the command in the `myrepo` directory

	$ jekyll build
	$ jekyll serve

To view the website locally, go to [http://localhost:4000](http://localhost:4000). Afterwards you can press ctrl-c to stop the process in the terminal.

#### Editing the `_config.yml` file
When you open the `index.md` file included in the Jekyll-Boostrap download, it will tell you to edit the `_config.yml` file to add in all of the information about your project.  Open up the `_config.yml` file and change this information: 

	title : Jekyll Bootstrap
	tagline: Site Tagline
	author :
		  name : Name Lastname
		  email : blah@email.test
		  github : username
		  twitter : username
		  feedburner : feedname
		  
Also, you will want to change the `production_url` to change the `username` to your Github user name. 
	
	production_url : http://username.github.io/myrepo
	BASE_PATH : http://username.github.io/myrepo	

Add the following line into the `_config.yml` file to tell [GitHub how to interpret the markdown](https://help.github.com/articles/migrating-your-pages-site-from-maruku): 

	markdown: kramdown

New pages can be added using the `rake` command.  To keep the folder clean, make a new directory titled `/pages` and place the .md files in it.  

	$ mkdir pages
	$ rake page name="pages/contactme.md"
	
This will create a new markdown file named `contactme` in a new directory called `pages`.  Put all the markdown files in the `/pages` directory. 

Create and edit the Markdown files for your website, then commit your changes. 

	$ git add .
	$ git commit -m "initial page commit"

If this is repository is meant to be your User Page, you can use the `master` branch to publish your website.  If this is Project Page, change the name of the `master` branch to `gh-pages` and push to GitHub: 
	$ git branch -m master gh-pages 
	$ git remote add origin git@github.com:username/myrepo.git
	$ git push -u origin gh-pages

#### Jekyll-Bootstrap Themes

One of the best parts about using Jekyll-Bootstrap is the fact you can [pick themes or create themes for your website!](http://themes.jekyllbootstrap.com). To [install a new theme](http://jekyllbootstrap.com/usage/jekyll-theming.html), the general syntax is 

	$ cd myrepo
	$ rake theme:install git="newtheme.git"
	
This will place all the necessary files for the theme in your repository .  You can also switch between themes using `$ rake theme:switch name="cooltheme"`. 

The base themes for a `page` and `post` are found in `_includes/themes/twitter/`.  If are familiar with html and you want to make changes to the .html files, these are the files to edit. 

## Using Karl Broman's simple_site repository
Karl Broman has also provided a GitHub repository called `simple_site` (http://kbroman.github.io/simple_site/) which you can clone similar the repository from `jekyll-bootstrap`.  He has provided excellent documentation on creating both User Pages and Project Pages, so I refer you to his website for further details. Briefly, it works very similar to using the jekyll-bootstrap repository: 

	$ git clone git://github.com/kbroman/simple_site
	$ mv simple_site myrepo
	$ cd myrepo
	$ rm -rf .git
	$ git init 
	
Create and edit the Markdown files for your website, then commit your changes. 

	$ git add .
	$ git commit -m "initial page commit"

This is a very basic website, but you can edit the Markdown files to personalize it.  If this is repository is meant to be your User Page, you can use the `master` branch to publish your website.  If this is Project Page, change the name of the `master` branch to `gh-pages` and push to GitHub: 

	$ git branch -m master gh-pages 
	$ git remote add origin git@github.com:username/myrepo.git
	$ git push -u origin gh-pages

## Next: 
Create [special Project Pages](pages/orphan-ghpages.html) using `--orphan gh-pages` branches. This keeps the code for your project in the `master` branch, but all the files related to the website in an "orphan-ed" branch called `gh-pages` because it has no history from that point.  


## Additional Useful Resources
* [Quick start guide to using jekyll-bootstrap](http://jekyllbootstrap.com/usage/jekyll-quick-start.html) 
* [GitHub: Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages)
* [Get Started with GitHub Pages (Plus Bonus Jekyll) from Anna Debenham](http://24ways.org/2013/get-started-with-github-pages/)
* [Blogging with Jekyll and GitHub Pages](http://dmayance.com/blogging-with-jekyll-and-github-pages/)

