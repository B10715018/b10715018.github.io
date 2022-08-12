# aboutMe

A introductory page about me and build using SSG(Static Site Generator) which is Jekyll

# Pre-requisite

## To use Jekyll (A static site generator) Mac Development need to have Ruby installed in the mac environment

```
brew install ruby
```

## Install Jekyll

```
gem install jekyll bundler
```

## Create new Jekyll site

```
jekyll new {PROJECT_NAME}
```

## change directory into jekyll project

```
cd {PROJECT_NAME}
```

## To serve the static site generator:

```
bundle exec jekyll serve
```

## To serve live reload for the changes in the static site generator

```
bundle exec jekyll serve --livereload
```

## If unexpected error such as unable to load EventMachine C, then should reinstall EventMachine using Ruby

```
gem uninstall eventmachine
gem install eventmachine --platform ruby
bundle exec jekyll serve --livereload
```

## Gemfile is for the dependency used by Jekyll and Gemfile.lock is the detail version of Gemfile

## \_config.yml is the stores site setting which rarely changed variables

## Where as the \_site contained the generated site by Jekyll which we should not change

## \_post folder is where we edit the file to generate our static site

## change layout by creating \post folder in the base folder and create new markdown file with date slug format and insert the following:

```
---
layout: # specifies the layout to use for this file
title: # post name
date: # post publish date
categories: # the categories of this post. You can separate multiple categories using a single space
---
```

## create \_layouts folder in the base folder and create the markdown file called `post.html`

```
{% if page.title%}
	<h1>{{page.title}}</h1>
{% else %}
	<h1>Untitled post</h1>
{% endif %}
{{ page.date | date: "%b %d, %Y" }}
{{ content }}
```

Insert the following code snippet to override the default layout from the default post layout offered by the Jekyll

## create assets folder to put image for the static site

```
mkdir -p assets/images/welcome
```
