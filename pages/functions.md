---
layout: page
title: "Functions"
description: ""
---
{% include JB/setup %}


* Syntax
* Arguments
* Variables
* References
* Returns
* Variable Scope
* Anonymous Functions, closures

## Reasons

* Readability
* Maintainability
* Code separation
* Modularity
* Our Comp-Sci teacher told us to
* To do otherwise would subject us to mockery

* * *


## Features

{% highlight php5 linenos %}
<?php
function name() { }
{% endhighlight %}

* All functions in PHP return a value (null if return is not used).
* function names are not case-sensitive
* global $id; // GLOBALS[‘id’];
* PHP 5 allows default values to be specified for parameters even when they are declared as by-reference (if a variable is not passed in, a new one will be created)
* In PHP4 Objects were thrown around ByVal.
* In PHP5 Objects are always passed ByRef unless you explicitly clone it.
* Is "_" a valid function name?

{% highlight php5 linenos %}
<?php
function printList($string, $count = 5)

function newTo5(&$number = 2)

$a = func_get_args();

int func_num_args(void)

mixed func_get_arg ( int $arg_num )
{% endhighlight %}


* * *

## By reference

{% highlight php5 linenos %}
<?php
&function name() { }
{% endhighlight %}

* allows you to return a variable as the result of the function, instead of a copy
* is used for things like resources and when implementing the Factory pattern
* you must return a variable
* you cannot return an expression by reference
* you cannot return an empty return statement to force a NULL return value


* * *

## Anonymous Functions, closures

[http://php.net/manual/en/functions.anonymous.php](http://php.net/manual/en/functions.anonymous.php)

Аllow the creation of functions which have no specified name. They are most useful as the value of [callback](http://www.php.net/manual/en/language.pseudo-types.php#language.types.callback) parameters, but they have many other uses.

Closures can also be used as the values of variables; PHP automatically converts such expressions into instances of the `Closure` internal class. 

{% highlight php5 linenos %}
<?php
$greet = function($name)
{
    printf("Hello %s\r\n", $name);
};

$greet('World');
$greet('PHP');
?>
{% endhighlight %}

It is possible to use [func_num_args()](http://www.php.net/manual/en/function.func-num-args.php), [func_get_arg()](http://www.php.net/manual/en/function.func-get-arg.php), and [func_get_args()](http://www.php.net/manual/en/function.func-get-args.php) from within a closure. 

The predefined final class `Closure` was introduced in PHP 5.3.0. It is used for internal implementation of [anonymous functions](http://www.php.net/manual/en/functions.anonymous.php).
The class has a constructor forbidding the manual creation of the object (issues `E_RECOVERABLE_ERROR`) and the `__invoke` method with the calling magic.

May also inherit variables from the parent scope.

{% highlight php5 linenos %}
<?php
$callback =
            function ($quantity, $product) use ($tax, &$total)
            {
                $pricePerItem = constant(__CLASS__ . "::PRICE_" .
                    strtoupper($product));
                $total += ($pricePerItem * $quantity) * ($tax + 1.0);
            };
        
        array_walk($this->products, $callback);
{% endhighlight %}
