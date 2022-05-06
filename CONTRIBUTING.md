# Contribution Guideline

This repository contains the sources from which the statical Webpage hosted at 
(FAIR Data Commons - Service Portfolio)[https://kit-data-manager.github.io/webpage/] is build. The deployment process is 
automatically triggered at each push to the `gh-pages` branch. Therefor, the static site generator [Jekyll](https://jekyllrb.com/)
is used. If you plan to extend the Webpage, it is recommended to install Jekyll locally on your machine in order to be able 
to test the resulting page before publishing it. More information on how to install Jekyll can be found in the 
[Quickstart section](https://jekyllrb.com/docs/) of their Webpage.

As soon as you've successfully installed Jekyll, you can clone this repository to your local machine and switch to the `gh-pages`
branch:

```
user@localhost:/home/user/$ git clone https://github.com/kit-data-manager/webpage.git
[...]
user@localhost:/home/user/$ cd webpage
user@localhost:/home/user/webpage/$ git checkout gh-pages
```

You may also fork the entire repository in case you don't have permissions for pushing to the repository directly or if you want
to be on the safe side without the risk to break anything.

If you've installed Jekyll properly, you should now be able to build and serve the Webpage locally the first time:

```
user@localhost:/home/user/webpage/$ bundle install
[...]
user@localhost:/home/user/webpage/$ bundle exec jekyll serve 
Configuration file: /home/user/webpage/_config.yml
            Source: /home/user/webpage/webpage
[...]
```

With the test instance running, you can now start adding your content. This can be done while the instance is running, as 
Jekyll will rebuild on every change allowing you the see all updated after refreshing the page in the Browser. However,
this does not apply if you change any global information which you can find in `_config.yml`. Changed to this file require a 
full restart of the instance.

## Structure of the Webpage

The project is structured as specified by Jekyll. In the root folder, you'll find the main index pages as well as 
the file `_config.yml`, which contains the site configuration, e.g. the general page title, domain information and the 
theme selection. For extending the Webpage, the most relevant part of `_config.yml` is the `collections` definition, 
which defines, which sub-folders are used to generated HTML pages from Markdown files. The definition may look as follows: 

```
collections:
  base-repo:
    output: true
```
This snippet defines, that Jekyll will look in the project's root for a folder `_base-repo` and will generate HTML output files,
no matter whether the files are referenced anywhere on the Webpage or not. If the `output` property is omitted, the files of this
collection are only rendered if the collection is directly addressed in one of the sub-pages, e.g., by iteration through it using 
a [Liquid](https://shopify.github.io/liquid/) template.

### Sub-Pages using Collections

As mentioned before, collections are used to define sub-folders which are scanned for Markdown files used to generate static
Webpages by Jekyll. In the `_example` folder you can inform yourself how such a sub-page may look like.   

