---
layout: page
title: "Strings & Patterns"
description: ""
---
{% include JB/setup %}

{% include menu/strings-and-patterns.md %}

* * * 

## Functions


* `int strlen ( string $string )`
* `int strpos ( string $haystack , mixed $needle [, int $offset = 0 ] )` - return the position of the search string within the target
* `int stripos ( string $haystack, string $needle [, int $offset] )`
* `int strrpos ( string $haystack, string $needle [, int $offset] )`
* `string strstr ( string $haystack , mixed $needle [, bool $before_needle = false ] )` - return the portion of target from the beginning of the first match until the end
* `string stristr ( string $haystack, string $needle )`
* `int strspn ( string $subject , string $mask [, int $start [, int $length ]] )` - returns the number of characters matching the mask
* `int strcspn ( string $str1 , string $str2 [, int $start [, int $length ]] )` - uses a blacklist and returns the number of non-matching characters
* `string setlocale ( int $category, string $locale [, string $...] )`
* `string str_pad ( string $input , int $pad_length [, string $pad_string = " " [, int $pad_type = STR_PAD_RIGHT ]] )`
* `string strrev ( string $string )` - Reverse a string


* * *

## Escape Sequences


* `\n` linefeed (LF or 0x0A (10) in ASCII)
* `\r `carriage return (CR or 0x0D (13) in ASCII)
* `\t` horizontal tab (HT or 0x09 (9) in ASCII)
* `\\` backslash
* `\$` dollar sign
* `\"` double-quote
* `\[0-7]{1,3}` the sequence of characters matching the regular expression is a character in octal notation


* * *

## Matching Strings


* `int strcmp ( string $str1 , string $str2 )` - Returns < 0 if str1 is less than str2 ; > 0 if str1 is greater than str2 , and 0 if they are equal.
* `int strcasecmp ( string $str1 , string $str2 )` – case insensitive version of strcmp()
* `int strncasecmp ( string $str1 , string $str2 , int $len )`
* `0 == FALSE` and `0 !== FALSE`


* * *

## Extracting


* `string substr ( string $string , int $start [, int $length ] )` - to retrieve a portion of a string
* Array Syntax
* The `{}` syntax is depreciated in PHP 5.1 and will produce a warning under `E_STRICT`


* * *

## Formatting


* sometimes governed by locale considerations
* `string number_format ( float $number , int $decimals , string $dec_point , string $thousands_sep )` – by default formats a number with the comma as the thousands separator, and no decimal
* `string money_format ( string $format , float $number )` – only available when the underlying c library `strfmon()` is available (not windows)


* * *

## Print Family


* `int print ( string $arg )` - Outputs arg. (language construct)
* `int printf ( string $format [, mixed $args [, mixed $... ]] )` - Output a formatted string
* `string sprintf ( string $format [, mixed $args [, mixed $... ]] )` - Return a formatted string
* `int vprintf ( string $format , array $args )` - Display array values as a formatted string according to format
* `mixed sscanf ( string $str , string $format [, mixed &$... ] )` - http://ru2.php.net/sscanf
* `mixed fscanf ( resource $handle , string $format [, mixed &$... ] )` - Parses input from a file according to a format


* * *

## Printf Formatting Specifiers

* `%` - a literal percent character. No argument is required.
* `b` - the argument is treated as an integer, and presented as a binary number.
* `c` - the argument is treated as an integer, and presented as the character with that ASCII value.
* `d` - the argument is treated as an integer, and presented as a (signed) decimal number.
* `e` - the argument is treated as scientific notation (e.g. `1.2e+2`).
* `u` - the argument is treated as an integer, and presented as an unsigned decimal number.
* `f` - the argument is treated as a float, and presented as a floating-point number (locale aware).
* `F` - the argument is treated as a float, and presented as a floating-point number (non-locale aware). Available since PHP 4.3.10 and PHP 5.0.3.
* `o` - the argument is treated as an integer, and presented as an octal number.
* `s` - the argument is treated as and presented as a string.
* `x` - the argument is treated as an integer and presented as a hexadecimal number (with lowercase letters).
* `X` - the argument is treated as an integer and presented as a hexadecimal number (with
uppercase letters).


* * *

## Replacement

* `mixed str_replace ( mixed $search , mixed $replace , mixed $subject [, int &$count ] )`
* `mixed str_ireplace ( mixed $search, mixed $replace, mixed $subject [, int &$count] )`
* `mixed substr_replace ( mixed $string, string $replacement, int $start [, int $length] )`
* `string strtr ( string $str, string $from, string $to )`


* * *

## PCRE(Perl Compatible Regular Expressions) – Meta Characters

* `\d` Digits 0-9
* `\D` Anything not a digit
* `\w` Any alphanumeric character or an underscore (_)
* `\W` Anything not an alphanumeric character or an underscore
* `\s` Any whitespace (spaces, tabs, newlines)
* `\S` Any non-whitespace character
* `.` Any character except for a newline
* `?` Occurs 0 or 1 time
* `*` Occurs 0 or more times
* `+` Occurs 1 or more times
* `{n}` Occurs exactly n times
* `{,n}` Occurs at most n times
* `{m,}` Occurs m or more times
* `{m,n}` Occurs between m and n times


* * *

## PCRE – Pattern Modifiers


* `i` – Case insensitive search
* `m` – Multiline, $ and ^ will match at newlines
* `s` – Makes the dot metacharacter match newlines
* `x` – Allows for commenting
* `U` – Makes the engine un-greedy
* `u` – Turns on UTF8 support
* `e` – Matched with preg_replace() allows you to call

* `int preg_match ( string $pattern , string $subject [, array &$matches [, int $flags [, int $offset ]]] )` – Returns the number of matches found by a given search string
* `int preg_match_all ( string $pattern, string $subject, array &$matches [, int $flags [, int $offset]] )`
* `mixed preg_replace ( mixed $pattern , mixed $replacement , mixed $subject [, int $limit = -1 [, int &$count ]] )`
* `array preg_split ( string $pattern , string $subject [, int $limit = -1 [, int $flags = 0 ]] )`


* * *

## HEREDOC and NOWDOC

[http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.heredoc](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.heredoc)

As of PHP 5.3.0, it's possible to initialize static variables and class properties/constants using the Heredoc syntax.

PHP 5.3.0 also introduces the possibility for Heredocs to use double quotes in declarings.

Heredocs can not be used for initializing class properties. Since PHP 5.3, this limitation is valid only for heredocs containing variables.

{% highlight php5 linenos %}
<?php
$str = <<<EOD
Example of string
spanning multiple lines
using heredoc syntax.
EOD;

/* More complex example, with variables. */
class foo
{
    var $foo;
    var $bar;

    function foo()
    {
        $this->foo = 'Foo';
        $this->bar = array('Bar1', 'Bar2', 'Bar3');
    }
}

$foo = new foo();
$name = 'MyName';

echo <<<EOT
My name is "$name". I am printing some $foo->foo.
Now, I am printing some {$foo->bar[1]}.
This should print a capital 'A': \x41
EOT;
?>
{% endhighlight %}

[http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.nowdoc](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.nowdoc)

Unlike heredocs, nowdocs can be used in any static data context. The typical example is initializing class properties or constants

A nowdoc is specified similarly to a heredoc, but no parsing is done inside a nowdoc.

A nowdoc is identified with the same `<<<` sequence used for heredocs, but the identifier which follows is enclosed in single quotes, e.g. `<<<'EOT'`. All the rules for heredoc identifiers also apply to nowdoc identifiers, especially those regarding the appearance of the closing identifier. 

