---
<center>How to Use Hugo<center>  
---


1.Overview

2.How to create a personal website with HUGO

3.How to publish  website on GitHub

----


 ## 1. Overview

### 1.1 What is Hugo

Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.

Hugo is a general-purpose website framework. Technically speaking, Hugo is a static site generator. Unlike systems that dynamically build a page with each visitor request, Hugo builds pages when you create or update your content. Since websites are viewed far more often than they are edited, Hugo is designed to provide an optimal viewing experience for your website’s end users and an ideal writing experience for website authors.



We think of Hugo as the ideal website creation tool with nearly instant build times, able to rebuild whenever a change is made.

### 1.2 Hugo Features

Hugo boasts blistering speed, robust content management, and a powerful templating language making it a great fit for all kinds of static websites.

## 2. How to create a personal website with HUGO

### 2.1 Installing Hugo

Hugo is available as a single binary. You can install Hugo two ways: using a package manager, or by downloading the binary manually and placing it in a global location so you can run it anywhere.

Package managers are utilities that let you install and remove programs and utilities. Linux systems often have a built-in package manager. If you’re running macOS, you can install the Homebrew package manager. If you’re using Windows, you can install Chocolatey. Finally, Linux users can install Linuxbrew,a version of Homebrew for Linux that offers more up-to-date packages than the package manager that comes with their system.

Installation via a package manager is the easiest method, although you might not always get the most recent version.

If you’re using a Mac and you have Homebrew installed, you can install the extended version of Hugo with:

```shell
brew install hugo
```

On Windows,  you can install Hugo like this
1. Download the installation package from HUGO's GitHub repository and use it.I am using the version of hugo_0.83.1_Windows-64bit.zip.After downloading and unzipping, add it to the PATH of the system environment variable of Windows. No installation is required.
2. Verify that HUGO has been successfully installed: HUGO Version

Hugo is installed and ready. Let’s use it to build a basic site.

### 2.2 Creating Your Site

Hugo has a built-in command that generates a website project for you; this includes all of the files and directories you need to get started.

Execute the following command to tell Hugo to create a new site named `quickstart`:

```shell
hugo new site quickstart
```

This creates the portfolio directory, with the following files and directories within:

 	quickstart/
 	├── archetypes
 	├── config.toml
 	├── content
 	├── data
 	├── layouts
 	├── static
 	└── themes


In your terminal, switch to the newly created `quickstart ` directory:

```shell
cd quickstart
```

Take a look at the site’s configuration file. Open the config.toml file in your text editor. You’ll see the following text:

```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
```

This file is written in TOML[^4] a configuration format designed to be easy to read and modify. The default configuration file only has a handful of data, but you’ll add more as you build out your site.

### 2.3 Adding a theme

See [themes.gohugo.io](https://themes.gohugo.io/) for a list of themes to consider. This quickstart uses the beautiful [Ananke theme](https://themes.gohugo.io/gohugo-theme-ananke/).

First, download the theme from GitHub and add it to your site’s `themes` directory:

```bash
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```

*Note for non-git users:*

- If you do not have git installed, you can download the archive of the latest version of this theme from: https://github.com/theNewDynamic/gohugo-theme-ananke/archive/master.zip
- Extract that .zip file to get a “gohugo-theme-ananke-master” directory.
- Rename that directory to “ananke”, and move it into the “themes/” directory.

Then, add the theme to the site configuration in `config.toml` file:

```
theme = "ananke"
```

### 2.4 Adding some contents

You can manually create content files (for example as `content/<CATEGORY>/<FILE>.<FORMAT>`) and provide metadata in them, however you can use the `new` command to do a few things for you (like add title and date):

```
hugo new posts/How-to-use-hogo.md
```

Edit the newly created content file if you want, it will start with something like this:

```markdown
---
title: "How to Use Hugo "
date: 2021-05-11T17:33:42+08:00
draft: true
---
```

> Drafts do not get deployed; once you finish a post, update the header of the post to say `draft: false`.

### 2.5 Starting the Hugo server

Now, start the Hugo server with drafts enabled:

```
▶ hugo server -D

                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  1
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Total in 11 ms
Watching for changes in /Users/bep/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /Users/bep/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

**Navigate to your new site at http://localhost:1313/.**

Feel free to edit or add new content and simply refresh in browser to see changes quickly (You might need to force refresh in webbrowser, something like Ctrl-R usually works).

## Building static pages

After running `hugo server` for local web development, you need to do a final `hugo` run *without the `server` part of the command* to rebuild your site. You may then deploy your site by copying the `public/` directory to your production web server.

```
hugo -D
```

Output will be in `./public/` directory by default (`-d`/`--destination` flag to change it, or set `publishdir` in the config file).

## Deploying your website

Since Hugo generates a static website, your site can be hosted *anywhere* using any web server. 

Deploy Hugo as a GitHub Pages project or personal/organizational site and automate the whole process with Github Action Workflow

GitHub provides free and fast static hosting over SSL for personal, organization, or project pages directly from a GitHub repository via its [GitHub Pages service](https://help.github.com/articles/what-is-github-pages/) and automate development workflows and build with [GitHub Actions](https://docs.github.com/en/actions).

### Assumptions

1. You have Git 2.8 or greater [installed on your machine](https://git-scm.com/downloads).
2. You have a GitHub account. [Signing up](https://github.com/join) for GitHub is free.
3. You have a ready-to-publish Hugo website.

### Types of GitHub Pages

There are two types of GitHub Pages:

- User/Organization Pages (`https://<USERNAME|ORGANIZATION>.github.io/`)
- Project Pages (`https://<USERNAME|ORGANIZATION>.github.io/<PROJECT>/`)

Please refer to the [GitHub Pages documentation](https://help.github.com/articles/user-organization-and-project-pages/#user--organization-pages) to decide which type of site you would like to create as it will determine which of the below methods to use.

### GitHub User or Organization Pages

As mentioned in the [GitHub Pages documentation](https://help.github.com/articles/user-organization-and-project-pages/#user--organization-pages), you can host a user/organization page in addition to project pages. Here are the key differences in GitHub Pages websites for Users and Organizations:

1. You must use a `<USERNAME>.github.io` to host your **generated** content
2. Content from the `main` branch will be used to publish your GitHub Pages site

This is a much simpler setup as your Hugo files and generated content are published into two different repositories.

You can start by creating a Repository on GitHub called `test20210513.github. IO` (replace `coderzh` with your GitHub user name).

Execute the Hugo command at the root of the site to generate the final page:

```shell
hugo  --baseUrl="http://test20210513.github.io/"
```

> Note that the above command does not generate a draft page. If no articles are generated, update `draft=false` from the header and rebuild.

All files in the pubilc directory will be pushed to the master branch of the newly created Repository.

```shell
cd public
git init
git remote add origin https://github.com/test20210513/test20210513.github.io.git
git add -A
git commit -m "first commit"
git push -u origin master
```

Finally, visit: http://test20210513.github.io/ on you browser.





