## Overview

### What is Hugo

Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.

Hugo is a general-purpose website framework. Technically speaking, Hugo is a static site generator. Unlike systems that dynamically build a page with each visitor request, Hugo builds pages when you create or update your content. Since websites are viewed far more often than they are edited, Hugo is designed to provide an optimal viewing experience for your website’s end users and an ideal writing experience for website authors.

Websites built with Hugo are extremely fast and secure. Hugo sites can be hosted anywhere, including [Netlify](https://netlify.com/), [Heroku](https://www.heroku.com/), [GoDaddy](https://www.godaddy.com/), [DreamHost](https://www.dreamhost.com/), [GitHub Pages](https://pages.github.com/), [GitLab Pages](https://about.gitlab.com/features/pages/), [Surge](https://surge.sh/), [Aerobatic](https://www.aerobatic.com/), [Firebase](https://firebase.google.com/docs/hosting/), [Google Cloud Storage](https://cloud.google.com/storage/), [Amazon S3](https://aws.amazon.com/s3/), [Rackspace](https://www.rackspace.com/cloud/files), [Azure](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website), and [CloudFront](https://aws.amazon.com/cloudfront/) and work well with CDNs. Hugo sites run without the need for a database or dependencies on expensive runtimes like Ruby, Python, or PHP.

We think of Hugo as the ideal website creation tool with nearly instant build times, able to rebuild whenever a change is made.

### Hugo Features

Hugo boasts blistering speed, robust content management, and a powerful templating language making it a great fit for all kinds of static websites.

## Installing Hugo

Hugo is available as a single binary. You can install Hugo two ways: using a package manager, or by downloading the binary manually and placing it in a global location so you can run it anywhere.

Package managers are utilities that let you install and remove programs and utilities. Linux systems often have a built-in package manager. If you’re running macOS, you can install the Homebrew[^1] package manager. If you’re using Windows, you can install Chocolatey. Finally, Linux users can install Linuxbrew,[^2] a version of Homebrew for Linux that offers more up-to-date packages than the package manager that comes with their system.

Installation via a package manager is the easiest method, although you might not always get the most recent version.

If you’re using a Mac and you have Homebrew installed, you can install the extended version of Hugo with:

```shell
brew install hugo
```

On Windows, if you have Chocolatey[^3] installed, you can install Hugo with this command:

```shell
choco install -y hugo-extended
```

To install Hugo manually, find the extended version’s binary for your operating system on the [Hugo Releases](https://github.com/gohugoio/hugo/releases) page on GitHub. For example, if you’re on Windows, you’re looking for a filename like hugo-extended-x.y.z-Windows-64bit.zip. Download the file.

Now that you’ve manually downloaded the file, you’ll want to add it to your PATH environment variable, which your command-line interface uses to determine where it can find executable programs. That way you can execute it without specifying the full directory location.

On macOS or Linux, copy the executable to /usr/local/bin, which is already included in your PATH environment variable by default.

On Windows 10, create the directory `C:\hugo\bin`. Copy the hugo.exe file you extracted to `C:\hugo\bin`, and then add that folder to your `PATH` environment variable. To do this, use the Windows Search and type “environment”. Choose the option for Edit Environment Variables for My Account. On the screen that appears, press the Environment Variables button, locate `PATH` in the System Variables section, and press the Edit button. Add `C:\hugo\bin`. Press OK to save the settings, and then press OK on the rest of the dialogs to close them.

Once Hugo is installed, run the `hugo version` command from your command-line interface to ensure that Hugo is available in any directory on your system, and that you’ve installed the extended version:

```shell
hugo version
```

The hugo command has several subcommands that you’ll use as you build your site. You can see a list of all commands with `hugo help`.

```shell
hugo help
```

The output you see in your console should be similar to the following:

```
hugo is the main command, used to build your Hugo site.

Hugo is a Fast and Flexible Static Site Generator
built with love by spf13 and friends in Go.

Complete documentation is available at https://gohugo.io/.

Usage:
  hugo [flags]
  hugo [command]

Available Commands:
  check       Contains some verification checks
  config      Print the site configuration
  convert     Convert your content to different formats
  env         Print Hugo version and environment info
  gen         A collection of several useful generators.
  help        Help about any command
  import      Import your site from others.
  list        Listing out various types of content
  new         Create new content for your site
  server      A high performance webserver
  version     Print the version number of Hugo

Flags:
  -b, --baseURL string         hostname (and path) to the root, e.g. https://spf13.com/
  -D, --buildDrafts            include content marked as draft
  -E, --buildExpired           include expired content
  -F, --buildFuture            include content with publishdate in the future
      --cacheDir string        filesystem path to cache directory. Defaults: $TMPDIR/hugo_cache/
      --cleanDestinationDir    remove files from destination not found in static directories
      --config string          config file (default is path/config.yaml|json|toml)
      --configDir string       config dir (default "config")
  -c, --contentDir string      filesystem path to content directory
      --debug                  debug output
  -d, --destination string     filesystem path to write files to
      --disableKinds strings   disable different kind of pages (home, RSS etc.)
      --enableGitInfo          add Git revision, date and author info to the pages
  -e, --environment string     build environment
      --forceSyncStatic        copy all files when static is changed.
      --gc                     enable to run some cleanup tasks (remove unused cache files) after the build
  -h, --help                   help for hugo
      --i18n-warnings          print missing translations
      --ignoreCache            ignores the cache directory
  -l, --layoutDir string       filesystem path to layout directory
      --log                    enable Logging
      --logFile string         log File path (if set, logging enabled automatically)
      --minify                 minify any supported output format (HTML, XML etc.)
      --noChmod                don't sync permission mode of files
      --noTimes                don't sync modification time of files
      --path-warnings          print warnings on duplicate target paths etc.
      --quiet                  build in quiet mode
      --renderToMemory         render to memory (only useful for benchmark testing)
  -s, --source string          filesystem path to read files relative from
      --templateMetrics        display metrics about template executions
      --templateMetricsHints   calculate some improvement hints when combined with --templateMetrics
  -t, --theme strings          themes to use (located in /themes/THEMENAME/)
      --themesDir string       filesystem path to themes directory
      --trace file             write trace to file (not useful in general)
  -v, --verbose                verbose output
      --verboseLog             verbose logging
  -w, --watch                  watch filesystem for changes and recreate as needed

Use "hugo [command] --help" for more information about a command.
```

Hugo is installed and ready. Let’s use it to build a basic site.

## Creating Your Site

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
Each of these directories has a specific purpose:

+ archetypes

  The archetypes directory is where you place Markdown templates for various types of content. An “archetype” is an original model or pattern that you use as the basis for other things of the same type. Hugo uses the files in the archetypes folder as models when it generates new content pages. There’s a default one that places a title and date in the file and sets the draft status to true. You’ll create new ones later.

+ config.toml

  The config.toml file holds configuration variables for your site that Hugo uses internally when constructing your pages, but you can also use values from this file in your themes. For example, you’ll find the site’s title in this file, and you can use that in your layout.

+ content

  The content directory holds all of the content for your site. You can organize your content in subdirectories like posts, projects, and videos. Each directory would then contain a collection of Markdown or HTML documents.

+ data

  The data directory holds data files in YAML, JSON, or TOML. You can load these data files and extract their data to populate lists or other aspects of your site.

+ layouts

  The layouts folder is where you define your site’s look and feel.

+ static

  The static directory holds your CSS, JavaScript files, images, and any other assets that aren’t generated by Hugo.

+ themes

  The themes directory holds any themes you download or create. You can use the layouts folder to override or extend a theme you’ve downloaded.

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

Hugo’s internal functions use the baseURL value to build absolute URLs. If you have a domain name for your site, you should change this value to reflect that domain. In this document, you’ll use relative URLs, so you can leave this value alone until you’re ready to deploy your site to production.

The title value is where you’ll store the site’s title. You’ll use this value in your layouts, so change it from its default value:

```
baseURL = "http://example.org/"
languageCode = "en-us"
title = "Build WetSites With Hugo"
```

## Adding a theme

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


## Adding some contents

You can manually create content files (for example as `content/<CATEGORY>/<FILE>.<FORMAT>`) and provide metadata in them, however you can use the `new` command to do a few things for you (like add title and date):

```
hugo new posts/my-first-post.md
```


Edit the newly created content file if you want, it will start with something like this:

```markdown
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---
```

> Drafts do not get deployed; once you finish a post, update the header of the post to say `draft: false`.

Hugo allows you to set `draft`, `publishdate`, and even `expirydate` in your content’s [front matter](https://gohugo.io/content-management/front-matter/). By default, Hugo will not publish:

1. Content with a future `publishdate` value
2. Content with `draft: true` status
3. Content with a past `expirydate` value

All three of these can be overridden during both local development *and* deployment by adding the following flags to `hugo` and `hugo server`, respectively, or by changing the boolean values assigned to the fields of the same name (without `--`) in your [configuration](https://gohugo.io/getting-started/configuration/):

1. `--buildFuture`
2. `--buildDrafts`
3. `--buildExpired`

## Starting the Hugo server

Now, start the Hugo server with drafts enabled:


```
▶ hugo server -D

                   | EN
+------------------+----+
  Pages            | 10
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  3
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

You can start by creating a Repository on GitHub called `test20210513.github. IO` (replace `test20210513` with your GitHub user name).

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

### Build Hugo With GitHub Action 

GitHub execute your software development workflows. Everytime you push your code on the Github repository, Github Action will build the site automatically.

Create a file in `.github/workflows/gh-pages.yml` containing the following content (based on https://github.com/marketplace/actions/hugo-setup ):

```yml
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy

jobs:
  deploy:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

For more advanced settings https://github.com/marketplace/actions/hugo-setup.

### Use a Custom Domain

If you’d like to use a custom domain for your GitHub Pages site, create a file `static/CNAME`. Your custom domain name should be the only contents inside `CNAME`. Since it’s inside `static`, the published site will contain the CNAME file at the root of the published site, which is a requirement of GitHub Pages.

Refer to the [official documentation for custom domains](https://help.github.com/articles/using-a-custom-domain-with-github-pages/) for further information.



[^1]:https://brew.sh
[^2]:https://docs.brew.sh/Homebrew-on-Linux
[^3]:https://chocolatey.org
[^4]:https://github.com/toml-lang/toml

