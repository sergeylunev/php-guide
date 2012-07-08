---
layout: page
title: "Object Oriented Programming"
description: ""
---
{% include JB/setup %}

{% include menu/oop.md %}


* * *

## Facts


* Prior to PHP5 OOP was a hack on top of the array implementation
* Slower than procedural code, but allows complex tasks to be understood more readily
* Objects are now dealt with by reference rather than by value, objects must be explicitly cloned to be copied


* * *

## PPP & F


* Public – Method or property can be accessed externally
* Private – Method or property is private to that class and can not be accessed externally
* Protected – Method or property is private and can also be accessed by extending classes
* Final – Method can not be overridden by extending classes


* * *

## Constants, Static


* are accessible as part of a class itself
* calling static properties using object notation will result in a notice
* by default the static method or property is considered public
* Class constants are public, and accessible from all scopes
* constants can only contain scalar values
* much cleaner code
* significantly faster than those declared with the define() construct


* * *

## Interfaces & Abstract Classes


* New feature added to PHP 5
* used to create a series of constraints on the base design of a group of classes
* You must declare a class as abstract so long as it has (or inherits without providing a body) at least one abstract method.
* a class can only extend one parent class, but it can implement multiple interfaces.


* * *

## Instanceof


Allows you to inspect all of the ancestor classes of your object, as well as any interfaces


* * *

## Autoloading

{% highlight php5 linenos %}
<?php
function __autoload($class_name)
{
    require_once "/www/phpClasses/{$class_name}.inc.php";
}
$a = new friend;
{% endhighlight %}


* * *

## Special Functions


* <http://php.net/manual/en/language.oop5.magic.php>
* `__construct()`
* `__destruct()` - Destruction occurs when all references to an object are gone, and this may not necessarily take place when you expect it or even when you want it to.
* `__toString()`
* `__sleep()`
* `__wakeup()`
* `__call()`
* `__get()`
* `__set()`


* * *

## Exceptions


* Unified method of error handling
* Makes proper error handling possible
* Can be accomplished with try catch blocks or by setting a unified error handler once
* Try catch blocks take precedence if the error raising code is within them
* are objects, created (or “thrown”) when an error occurs
* All unhandled exceptions are fatal.
* `catch()` portion of the statement requires us to hint the type of Exception
* `callback set_exception_handler ( callback $exception_handler )`
* `bool restore_exception_handler ( void )`


* * *

## SPL


* allow to stack autoloaders on top of each other
* `void spl_autoload ( string $class_name [, string $file_extensions = spl_autoload_extensions() ] )`
* `string spl_autoload_extensions ([ string $file_extensions ] )`
* `bool spl_autoload_register ([ callback $autoload_function [, bool $throw = true [, bool $prepend = false ]]] )` - first call to this function replaces the __autoload() call in the engine with its own implementation


* * *

## Reflection API


* <http://php.net/reflection>
* provides a manner to obtain detailed information about code
* `$func = new ReflectionFunction($func);`
* `ReflectionClass`
* `ReflectionMethod`
* `array get_defined_functions ( void )`
* `array get_object_vars ( object $object )`


* * *

## Type Hinting

<http://www.php.net/manual/en/language.oop5.typehinting.php>


* * *

## Late Static Binding

<http://php.net/manual/en/language.oop5.late-static-bindings.php>