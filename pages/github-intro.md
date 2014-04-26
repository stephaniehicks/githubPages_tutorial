---
layout: page
title: GitHub and GitHub Pages
description: 
---
{% include JB/setup %}

## git and GitHub
There are so many great reasons to use [git](http://git-scm.com) and [GitHub](https://github.com). My personal favorite tutorial is by Karl Broman called [git/github](http://kbroman.github.io/github_tutorial/) which I highly recommend if you are interested in learning more about git and GitHub.  

## GitHub Pages
[GitHub Pages](https://pages.github.com) is a really useful resource provided and hosted by GitHub. Here are a few examples of GitHub Pages: 

* Write programming books using GitHub and Markdown using [GitBook](http://www.gitbook.io)

* Turn R Markdown files into Markdown files using Knitr in R-Studio and make an [online book](http://genomicsclass.github.io/book/)

The purpose of GitHub Pages is to provide the GitHub user a way to create personal websites for themselves and websites for their projects / repositories. For each registered GitHub account (representing a user or an organization) you can register **one** User Page, but an **unlimited** Project pages. This User Page is a website that will have the domain name `http://username.github.io` or `http://username.github.com` where `username` is replaced by your GitHub username.  The Project Pages are websites which are special repositories that will have the domain name `http://username.github.io/myrepo` where the name of the repository on GitHub is called `myrepo`.  


The amazing Karl Broman recently added another tutorial specifically for [creating GitHub Pages](http://kbroman.github.io/simple_site/) using his `simple_site` repository at (https://github.com/kbroman/simple_site).  This tutorial is similar, but uses the [Jekyll-Bootstrap](http://jekyllbootstrap.com) repository at (https://github.com/plusjade/jekyll-bootstrap) which can include additional themes.  The main idea of behind both of these repositories is [Jekyll](http://jekyllrb.com) discussed next.  


## Jekyll
[Jekyll](http://jekyllrb.com) is a ["a simple blog aware, static site generator"](http://jekyllbootstrap.com/lessons/jekyll-introduction.html) based on files such as [Markdown](http://daringfireball.net/projects/markdown/). Many blogs are written in Jekyll including [every GitHub page](https://help.github.com/articles/using-jekyll-with-pages).  Therefore, it is definitely worth taking the time to understand a little bit about Jekyll, but it can be confusing if you are unfamiliar with it.  [Jekyll-Bootstrap](http://jekyllbootstrap.com) takes away a lot of the hassle about Jekyll by allowing the user to create blog-aware websites using markdown with [themes](http://themes.jekyllbootstrap.com). 

When you use Jekyll you will be installing a set of files in your GitHub repository that tell GitHub to create html files from the markdown files.  Jekyll-Bootstrap works the same way, except you will now have cool themes to pick from for your website! 

Before we discuss more about Jekyll, let's discuss the difference between a `user page` and `project pages`.  


## User Pages
To get a `user page`, you must create a repository on GitHub named `username.github.io` where `username` is replaced by your GitHub username. Once the repository is created on GitHub, you can use the [automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator) or use your own .html files.  All the files in the **master** branch of this repository are used to publish the website. 

If you used the automatic page generator, use `git init` to initialize the git repository, and fetch the files from GitHub: 

	$ mkdir username.github.io
	$ cd username.github.io
	$ git init
	$ git remote add origin git@github.com:username/username.github.io
	$ git fetch origin
	$ git checkout master
	$ git pull origin master
	
Note: we are using `git checkout` to check out the `master` branch because this is a `user page`.  When you use the automatic page generator for `project pages`, you will check out the **gh-pages**. 	
	
Next, you can edit the files in your `username.github.io` repository. Once you are happy with the files, use `git add` to track all the files you want tracked, use `git commit` to commit the files and push to GitHub: 

	$ git add .
	$ git commit -m "initial commit of user page"
	$ git push	

Don't worry if it takes a few minutes for the page to show up because there may be a delay up to ten minutes the first time you push the files to GitHub. 	


## Project Pages

To create a `project page`, you don't have to have actually create a `user site` if you don't want to, but the URL will still be `http://username.github.io/myrepo`.  Create a repository on GitHub. To illustrate the examples below, I will use the name `myrepo`, but you should change the name from `myrepo` to whatever is the name of your repository.  `Project pages` are different than a `user page` in the sense all the files related to creating the website are kept in a branch called the **gh-pages** branch (not in the **master** branch for a `user page`). You can use the [automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator) for `project pages` (similar to a `user page`) or again use your own .html files.  

If you used the automatic page generator,  use `git init` to initialize the git repository, and fetch the files from GitHub: 

	$ cd myrepo
	$ git init
	$ git remote add origin git@github.com:username/myrepo.git
	$ git fetch origin
	$ git checkout gh-pages

Next, you can edit the files in your `myrepo` repository. Once you are happy with the files, use `git add` to track all the files you want tracked, use `git commit` to commit the files and push to GitHub: 

	$ git add .
	$ git commit -m "initial commit of project page"
	$ git push origin gh-pages
	
	
## Generating a user page or project pages not using the automatic page generator
If you are interested in creating a `user page` or `project pages` not using the [automatic page generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator) or you don't have your own .html files already created and you don't want to edit .html files directly, fear not!   The next section on [Setting up GitHub Pages with Jekyll](pages/githubpages-jekyll.html) will allow you to create your website in Markdown (.md) files, but publish in .html files.  

