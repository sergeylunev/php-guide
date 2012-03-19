---
title: Variables 
permalink: /php-basics/variables.html
layout: post 
category: PHP Basics
---

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

