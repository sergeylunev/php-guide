---
layout: page
title: PHP Study Guide
---
{% include JB/setup %}

## What?

Originally PHP Study Guide was a small project that provides step by step guide on information needed to pass PHP5.3 ZCE certification: [http://www.zend.com/en/services/certification/php-5-certification/](http://www.zend.com/en/services/certification/php-5-certification/).

For now it aims to go little bit beyond the Zend Certification and is a good place to start your experience with PHP5.3 or, if you are already an experienced web developer, to return to the basics and remember some details.

## Where?

At the moment project is placed at <http://zce.evercodelab.com/> and hosted on [GitHub.Pages](http://pages.github.com).

## Sources

All content is assembled from different sources and tutorials.

* Zend PHP 5.0 Certification Course by Paul Reinheimer
* Zend PHP 5 Certification Study Guide
* Zend PHP 5.3 Study Guide v1
* [Read The Web Blog](http://readtheweb.info/index.php?s=Zend+PHP+5+Certification+Exam&submit=Go)
* <http://www.php.net/manual/en/>
* <http://zend-php.appspot.com/>

Original guide was structured in Google Docs and then published as [pdf](http://victimofbabylon.com/zce-php-53-study-guide).

## Who?

Mainly project is done by me, [Roma Lapin](https://github.com/memphys) and supported by [Evercode Lab](http://www.evercodelab.com/).

## How to contribute

At first all content was assembled to be used for PHP5.3 ZCE certification. So it aimed to be short and kind of limited. For now feel free to contribute to it. All suggestions to content and design is appreciated.

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

* title – page title
* layout - usually it is "page"

Menus is stored in `_includes/menu`.
