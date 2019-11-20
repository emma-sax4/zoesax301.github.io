# zoesax301.github.io [![Build Status](https://travis-ci.com/emma-sax4/zoesax301.github.io.svg?branch=master)](https://travis-ci.com/emma-sax4/zoesax301.github.io)

#### Live site at: [https://zoesax301.emmasax4.info](https://zoesax301.emmasax4.info)

## Basic Information

For more information on contributing to this project, please see [CONTRIBUTING.md](https://github.com/emma-sax4/zoesax301.github.io/blob/master/.github/CONTRIBUTING.md).

To submit a feature request or a bug ticket, please use submit an official [GitHub Issue](https://github.com/emma-sax4/zoesax301.github.io/issues/new/choose).

For information on licensing, please see [LICENSE](https://github.com/emma-sax4/zoesax301.github.io/blob/master/LICENSE).

A brief reminder that this repository does have a standard [Code of Conduct](https://github.com/emma-sax4/zoesax301.github.io/blob/master/.github/CODE_OF_CONDUCT.md)... please follow it.

This page was originally generated using the [Architect Theme](https://github.com/jasonlong/architect-theme) theme by [Jason Long](https://twitter.com/jasonlong).

Currently, this site is monitored and maintained by Zoe's sister, [Emma](https://github.com/emma-sax4). Any questions about the site should be directed to her.

## Running Locally

To run this application locally, following these steps:
1. Be sure you have Ruby installed on your machine; the `.ruby-version` file specifies ruby 2.3.* because that's what's required for Jekyll and `github-pages` to run
2. First, bundle install and install all of the gems specified in the Gemfile:
    ```
    gem install bundler
    bundle install
    ```
3. Then build the site using Jekyll:
    ```
    jekyll build
    ```
4. Serve it up:
    ```
    jekyll serve
    ```
5. Navigate to the local URL Jekyll provides (`http://127.0.0.1:4000` on my machine)

NOTE: Running this process locally will most likely create at least one directory locally on your machine, such as `_site/`, `Gemfile.lock`, `.sass-cache/`, and potentially others. All of these are already in the `.gitignore`, but feel free to add others as necessary.

## Running Tests

This repository doesn't really have any tests at all (GitHub Pages is just a host of static site files, so there's no functionality to test). I do run TravisCI tests on every pull request and commit to master branch, but, as you can see from the [`.travis.yml`](https://github.com/emma-sax4/zoesax301.github.io/blob/master/.travis.yml), all the Travis run does is run `script: true`, so the builds will always pass (assuming `bundle` can properly install the dependencies as well).

## Deployments

GitHub automatically deploys each commit to master branch. A full deployment only takes a couple of minutes, but depending on what was changed (HTML files, images, etc), it can take up to about 5 minutes to propagate the changes. To make the changes appear faster, you can reload the entire website in incognito mode.

## Structure of this Project

Here are all of the parts of this project associated with running this application. This list does not include files/directories related to GitHub, Travis, Git, etc.
```
.
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   └── default.html
├── _pages
|   ├── page-01.md
|   ├── page-02.md
|   └── page-03.md
├── assets
|   ├── css
|   |   └── style.scss
|   ├── images
|   |   ├── favicon.ico
|   |   ├── logo-01.jpg
|   |   ├── logo-01.jpg
|   |   ├── picture-01.png
|   └── └── picture-02.png
├── _config.yml
├── Gemfile
└── index.md
```

Let's go through what each section does, from the top.

### `_includes/`

HTML files in this directory are for page elements, such as the header, footer, buttons, etc. Each element belongs in its own file. By placing these elements here, they can be reused on multiple pages without duplicating any code, and they reduce the clutter in busy pages. To call one of the elements, simply include the file in any other Markdown/HTML file:
```
{% include header.html %}
```

### `_layouts/`

HTML files in this directory are for the skeletons of a specific page. The `default.html` is the plainest of the plain. It includes the head, header, and footer, and defines the body and main content of the page. The other HTML files in the directory are for more detailed pages, such as the homepage and listing thoughts. To specify that a certain page should use a specific layout, write that as the `layout` in the top of any other Markdown/HTML file:
```
---
layout: default
.
.
.
---
```

### `_pages/`

These are the general pages in the top navigation bar of the site, although technically there are several other pages in there as well. They're written in Markdown, but Jekyll and liquid will use the Markdown content to make HTML files. The front matter of any Markdown/HTML file specifies the settings of the page:
```
---
layout: default # the layout HTML to use (required for EVERY page)
title: Page 1 # the title of this page (optional if the page is NOT in the nav bar)
order: 3 # the order of this page in the navigation bar (delete if the page is NOT in the nav bar)
permalink: /page1 # the static link this page should have (required for EACH page in this directory)
---
```

You can also specify custom settings that you want the page to have:
```
---
custom_field_1: true
custom_field_2: useful_string
---
```

Then, you can reference those custom settings on other HTML files (such as the layout the page is using... 😉):
```
{{ page.custom_field_1 }}
=> true
{{ page.custom_field_2 }}
=> useful_string
```

### `assets/`

This directory contains two subdirectories, `css/` and `images/`. `css/` only has one file—`stylesheet.scss`. This is where I can keep _all_ of the CSS that this project uses. To make sure it's all being used, there is one very important line in the `_includes/head.html`:
```
<link rel="stylesheet" type="text/css" href="assets/css/style.css" media="screen">
```

Without that line, none of the CSS would show up as expected.

`images/` gives me a place to store pictures, logos, the favicon, and other helpful documents. By putting them all into one directory, it provides some organization to the repository. To call a specific resource, you can either ask for it in HTML:
```
<div>
  <img src="/assets/images/picture-01.png" alt="Picture 1">
</div>
```

Or you can put a link to it in Markdown:
```
This is an example sentence, so it will throw a 404. See [here](../assets/images/logo-01.jpg)?
```

### `_config.yml`

This is where we tell Jekyll all of the configurations for this project. Each time this file is changed, restart your local Jekyll server to get the new changes.

### `Gemfile`

The Gemfile is where the application defines which Ruby gems are important to run the application. To learn how to use this file, see this [section](https://github.com/emma-sax4/zoesax301.github.io#running-locally).

### `index.md`

This is the first page that the site sees. Because of the way GitHub pages and Jekyll work, this is the only page that needs to be in the root directory of the project, and needs to be titled `index.md`. However, it's symlinked to the `_pages/home.md` file, so the only real place to edit that page should be through editing the `_pages/home.md` instead of the `index.md` file.
