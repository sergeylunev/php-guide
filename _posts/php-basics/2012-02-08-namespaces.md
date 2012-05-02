---
title: Namespaces
permalink: /php-basics/namespaces.html
layout: post 
category: PHP Basics
---

[http://www.php.net/manual/en/language.namespaces.php](http://www.php.net/manual/en/language.namespaces.php)

Solves two problems:

* Name collisions between code you create, and internal PHP classes/functions/constants or third-party classes/functions/constants.
* Ability to alias (or shorten) Extra_Long_Names designed to alleviate the first problem, improving readability of source code.

Only three types of code units are affected by namespaces: 

* classes
* functions
* constants. 

A file containing a namespace must declare the namespace at the top of the file before any other code - with one exception: the [declare](http://www.php.net/manual/en/control-structures.declare.php) keyword. 

Namespace name can be defined with sub-levels.

A class name can be referred to in three ways:

1.Unqualified name, or an unprefixed class name like `$a = new foo();` or `foo::staticmethod();`. If the current namespace is `currentnamespace`, this resolves to `currentnamespace\foo`. If the code is global, non-namespaced code, this resolves to `foo`. One caveat: unqualified names for functions and constants will resolve to global functions and constants if the namespaced function or constant is not defined. See [Using namespaces: fallback to global function/constant](http://www.php.net/manual/en/language.namespaces.fallback.php) for details.
2. Qualified name, or a prefixed class name like `$a = new subnamespace\foo();` or `subnamespace\foo::staticmethod();`. If the current namespace is `currentnamespace`, this resolves to `currentnamespace\subnamespace\foo`. If the code is global, non-namespaced code, this resolves to `subnamespace\foo`.
3. Fully qualified name, or a prefixed name with global prefix operator like `$a = new \currentnamespace\foo();` or `\currentnamespace\foo::staticmethod();`. This always resolves to the literal name specified in the code, `currentnamespace\foo`.

Two kinds of aliasing or importing: aliasing a class name, and aliasing a namespace name.

{% highlight php5 linenos %}
<?php
namespace my\name; // see "Defining Namespaces" section

class MyClass {}
function myfunction() {}
const MYCONST = 1;

$a = new MyClass;
$c = new \my\name\MyClass; // see "Global Space" section

$a = strlen('hi'); // see "Using namespaces: fallback to global
                   // function/constant" section

$d = namespace\MYCONST; // see "namespace operator and __NAMESPACE__
                        // constant" section
$d = __NAMESPACE__ . '\MYCONST';
echo constant($d); // see "Namespaces and dynamic language features" section
?>
{% endhighlight %}

{% highlight php5 linenos %}
<?php
namespace foo;
use My\Full\Classname as Another;

// this is the same as use My\Full\NSname as NSname
use My\Full\NSname;

// importing a global class
use \ArrayObject;

$obj = new namespace\Another; // instantiates object of class foo\Another
$obj = new Another; // instantiates object of class My\Full\Classname
NSname\subns\func(); // calls function My\Full\NSname\subns\func
$a = new ArrayObject(array(1)); // instantiates object of class ArrayObject
// without the "use \ArrayObject" we would instantiate an object of class foo\ArrayObject
?>
{% endhighlight %}
