ZCE-guide is a small project that provides step by step guide on information needed to pass PHP5.3 ZCE certification: [http://www.zend.com/en/services/certification/php-5-certification/](http://www.zend.com/en/services/certification/php-5-certification/).

Also, it is a good place to start your experience with PHP5.3 or, if you are already an experienced web developer, to return to the basics and remember some details.

Project uses [Jekyll](https://github.com/mojombo/jekyll) (blog-aware, static site generator in Ruby) with some staff from [Jekyll Bootstrap](http://jekyllbootstrap.com) and is hosted with [GitHub Pages](http://pages.github.com/).

If you want to contribute, please, read the following guide.

# How to contribute

## Workflow

In general, all development happens in master and topic branches. When changes are ready for publishing they are merged into gh-pages. GitHub processes new content and then automatically publishes it.

In order to contribute, please, do the following.

* [Fork the project](http://help.github.com/fork-a-repo/)
* Clone down your fork
* Create a topic branch to contain your change ( git checkout -b my_awesome_feature )
* Add some code
* Push the branch up ( git push origin my_awesome_feature )
* [Send a Pull Request](http://help.github.com/send-pull-requests/)

## Project layout and details

On the whole project follows standart [jekyll project layout](https://github.com/mojombo/jekyll/wiki/usage).

Each certification section is presented as page in `pages` directory. Each subsection is a part of a page.

Pygments is used for code highlighting.

Each page should have following variables in YAML Front Matter:

* title – post/page title
* layout - usually it is "page"

Menu is written in `_includes/menu.html`.

## Content

Original guide was structured in Google Docs and then published as [pdf](http://victimofbabylon.com/zce-php-53-study-guide). While the content transfer is happening, original doc is [available for anybody](https://docs.google.com/document/d/1GiLHFPV9dvLLsQfPj1f0WzYD1kBZ_EdAhspcxEEMWys/edit).

In order to help transfer contents from doc to this guide, please, do the following:

* Choose subsection to transfer
* Create an issue with subsection title in it and state that you are working on it.
* Format content using markdown as described earlier
* Send Pull Request
* Profit!

