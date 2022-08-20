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

## create data file

- To store data file like json, yml, csv we could create folder named `_data`

- and put all the csv, yml, json data there in the `_data` folder

- To access it type:

```
site.data.{file_name}
```

## conditional

- Used usually in navigation bar, to use:

```
{% if condition %}
  {{action}}
{% elsif condition%}
  {{action}}
{% else %}
  {{action}}
{% endif %}
```

## page and blog in jekyll all have front matter which could be accessed by themselves inside the project

- Example:

```
---
layout: ....
post: ....
---
```

- Some basic variables that are vital:
  `layout`: the layout that we will be using
  `title`: the title of the post
  `categories`: could be use to give URL path
  `permalink`: give a permanent link for our website

## The file `index.markdown` is where the home is

## For the draft content we can store it at the `_drafts` folder

- When we store the post in `_drafts` folder it would not be reload and if we would like it to be shown in the website:

```
jekyll serve --draft
```

## Creating page

- Blog is where we put the markdown file in the `_posts` folder

- While page is the markdown file which is located in the root folder

## Working with permalink

- We can put `permalink` in our page or blog in the front matter and some example:

```
categories: jekyll
permalink: "/:categories" # it will make path into "/jekyll"
```

## Working with default front end

- We can make default for our front matter by setting it on the `_config.yml`:

```
defaults:
	-
		scope:
			path: ""
			type: "post" # only project inside post folder will get this effect
		values:
			layout: "post" #default layout that we would like to use
			title: # change all the title if front matter is not specified
```

- Don't forget to restart your server everytime we change `_config.yml` file

## Working with Jekyll-theme

- Go to [Ruby website](https://rubygems.org) and search `jekyll-theme`

- Find for your suitable theme in the website

- To install the theme, go to our `Gemfile`:

```
gem "{YOUR_DESIRED_THEME}"
```

- And install the bundle:

```
bundle install
```

- And we would ready to go but check into that theme github and go to their `_layouts` folder and make sure to follow their avaiable layout like `default`, `post`, `page`

## Working with layouts

- The layouts basically can be modified by going to the `_layouts` folder and create the html file and the name based on the layout name that we would like to override.

- We can wrap a layout into the other layout through the content:

```
{{content}}
```

- We just need to make sure to put the front matter in the layout that we would like to wrap with our desired wrapper

## Dealing with variables

- We can access the variables from the layout or page by:

```
{{layout.title}}
{{page.title}} # title of the page or blog
{{site.title}} # title from the site level which is from the _config.yml
```

- [JekyllRB website](https://jekyllrb.com) Here we could find all the variables

## Dealing with include

- We could include part of components like navigation bar or title into every page or post by putting the components in the `_includes` folder

- Inside that folder we could create html file that could be by other page or blog or layout by:

```
{% include {COMPONENT_NAME}.html %}
```

- And while in the html file inside the `_includes` folder could take the color passed by the file that use that include by:

```
<h1 style="color: {{include.color}}">{{site.title}}</h1>
```

## Working with loops

- Syntax:

```
{% for post in site.posts %}
  {{ post.title }}<br>
{% endfor %}
```
