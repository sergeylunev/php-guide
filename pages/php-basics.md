---
layout: page
title: "Php Basics"
description: ""
---
{% include JB/setup %}

## PHP Tags

Standard Tags – best solution for portability and backwards compatibility, because they are guaranteed to be available and cannot be disabled by changing PHP’s configuration file:

{% highlight php5 linenos %}
<?php 
... code
?>
{% endhighlight %}

Short Tags - can be disabled (often for XML compliance) with short_open_tag directive in php.ini:

{% highlight php5 linenos %}
<?

?>
<?=$variable ?>
{% endhighlight %}

Script Tags:

{% highlight php5 linenos %}
<script language="php">
... code
</script>
{% endhighlight %}

ASP Tags - must be enabled specifically in the php.ini file via the asp_tags directive:

{% highlight php5 linenos %}
<%
... code
%>
<%=$variable; %>
{% endhighlight %}

* * *

## Comments

Single line comments are ended by either the newline character or a closing PHP tag. Latter can cause unintended output.

{% highlight php5 linenos %}
<?php
// This is a single line comment

# This is also a single line comment
{% endhighlight %}

{% highlight php5 linenos %}
<?php
/*
This is a multi-line
comment
*/
{% endhighlight %}

{% highlight php5 linenos %}
<?php
/**
* API Documentation Example
*
* @param string $bar
*/
function foo($bar) { }
{% endhighlight %}

* * *

## Operators

`>>` (Shift Right) – All of the bits in the binary number shift N places to the right in the number, the right most digit(s) falls out, and the resulting number is padded on the left with 0s. A right shift of one is equivalent to dividing a number by two, and tossing the remainder.

`<<` (Shift Left) – All of the digits shift N places to the left, padding the right with 0s. A left shift of one is equivalent to multiplying a number by two.

`` `command` `` (backticks) – Execute the contents as a shell command (shortcut for shell_exec()) with the same permissions as the webserver.

`Instanceof` – Returns true if the indicated variable is an instance of the designated class, one of it’s subclasses or a designated interface.

* * *

## Variables

### Naming:

* Can only contain letters, numbers or underscores
* Must start with a letter or an underscore

### Types

* Scalar types: boolean, string, integer, float.
* Compound types: array, object.
* Special Types: resource, null.

### Strings

Each character is represented by a single byte. PHP has no native support for multi-byte character sets (like Unicode).

Ordered collections of binary data.

Can be quoted in one of three ways:

* `'some text'` - characters within single quotes will be recorded as is, without variable or escape sequences interpreted and replaced
* `"some text"` – variables and escape sequences will be interpreted and replaced
* `<<<` – Heredoc functions in a similar manner to double quotes, but is designed to span multiple lines, and allow for the use of quotes without escaping.

{% highlight php5 linenos %}
<?php
$greeting = <<<GREETING
She said "That is $name's" dog!
While running towards the thief
GREETING;
{% endhighlight %}

### Integer

Can be specified in decimal (base 10), hexadecimal (base 16, precede with a 0x), or octal (base 8, precede with a 0) notation and optionally preceded by a sign (+, -)

The maximum size of an integer is platform dependent, a maximum of ~2Billion is common

### Float

`1.234, 1.2e3, 7E-10`

The size of a float is platform-dependent, although a maximum of `~1.8e308` with a precision of roughly 14 decimal digits is a common value

### Boolean

* Any integer other than 0 is cast to TRUE
* TRUE & FALSE are case-insensitive, though the all caps representation is common

### Arrays

Arrays can contain any combination of other variable types, even arrays or objects

### Objects

Objects allow data and methods to be combined into one cohesive structure

### Resource

Special variable that represents some sort of operating system resource, generally an open file or database connection.

While variables of the type resource can be printed out, their only sensible use is with the functions designed to work with them.

### null

* it has no value and no type
* is not the same as the integer zero or an zero length string (which would have types)

### Variable Variables

{% highlight php5 linenos %}
<?php
$a = 'name';
$$a = "Paul";
echo $name; //Paul
{% endhighlight %}

* * *

## Constants

Can not be changed once set.

{% highlight php5 linenos %}
<?php
define('ERROR', 'Something went wrong.');
const FOO = 'bar';
{% endhighlight %}

Only scalar.

* * *

## Controle Structures

### if

Alternate:

{% highlight php5 linenos %}
<?php
if ():
  ... 
else: 
  ... 
elseif:
  ... 
endif;
{% endhighlight %}

Short:

{% highlight php5 linenos %}
<?php
$expr ? true : false)
{% endhighlight %}

### switch

### while

### do

### for

continue

break

### foreach

### functions

Paramaters:

* Optional
* Byref
* Byval
* Objects
* Variable functions

### Objects

* * *

## Language Constructs

Elements that are built-into the language.

Do not have return value.

{% highlight php5 linenos %}
<?php
echo 'something'; 
die();
exit();
{% endhighlight %}

End a script in PHP5:

{% highlight php5 linenos %}
<?php
__halt_compiler()
die();
exit();
{% endhighlight %}

* * *

## Namespaces

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

1. Unqualified name, or an unprefixed class name like `$a = new foo();` or `foo::staticmethod();`. If the current namespace is `currentnamespace`, this resolves to `currentnamespace\foo`. If the code is global, non-namespaced code, this resolves to `foo`. One caveat: unqualified names for functions and constants will resolve to global functions and constants if the namespaced function or constant is not defined. See [Using namespaces: fallback to global function/constant](http://www.php.net/manual/en/language.namespaces.fallback.php) for details.
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

* * *

## Extensions

[http://devzone.zend.com/article/1021](http://devzone.zend.com/article/1021)

The PHP source bundle comes with around 86 extensions, having an average of about 30 functions each. Do the math, that's about 2500 functions. As if this weren't enough, [the PECL repository](http://pecl.php.net/) offers over 100 additional extensions, and even more can be found elsewhere on the Internet. 

* * *

## Config

[http://www.php.net/manual/en/configure.about.php](http://www.php.net/manual/en/configure.about.php)

[http://php.net/manual/en/configuration.php](http://php.net/manual/en/configuration.php)

* * *

## Performance. Bytecode caching

