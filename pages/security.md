---
layout: page
title: "Security"
description: ""
---
{% include JB/setup %}

{% include menu/security.md %}

* * *

## Levels


* Web Server level
* Data base level
* PHP itself


* * *

## Concepts


* "with great power comes great responsibility" (yeah)
* Defense in Depth - plan for failure; applications remain more resistant over time;
* Principle of Least Privilege
* Terms: Validation vs Escaping
   * Validation or Filtering is the process by which you subject data to a series of rules, either it passes (validates) or does not
   * Escaping is the process by which you prepare data for a specific resource by “escaping” certain portions of the data to avoid confusion of instruction and data


* * *

## Validate Input


One of three things can be said about received data:

* It is valid, the user entered the data you want, in the format you desire
* It is invalid because the user either did not comply or did not understand the rules on the data you requested (eg. Poorly formatted phone number)
* It is invalid because the user is attempting to compromise your system

* Data from the end user can not be trusted
* Validate data first don’t save it for last
* Fail early, tell the user what went wrong
* Whitelist vs Blacklist


* * *

## Functions


* `bool ctype_alnum ( string $text )` - Check for alphanumeric character(s)
* `ctype_alpha` - Check for alphabetic character(s)
* `ctype_cntrl` - Check for control character(s)
* `ctype_digit` - Check for numeric character(s)
* `ctype_graph` - Check for any printable character(s) except space
* `ctype_lower` - Check for lowercase character(s)
* `ctype_print` - Check for printable character(s)
* `ctype_punct` - Check for any printable character which is not whitespace or an alphanumeric character
* `ctype_space` - Check for whitespace character(s)
* `ctype_upper` - Check for uppercase character(s)
* `ctype_xdigit` - Check for character(s) representing a hexadecimal digit


* * *

## Register Globals


* Register globals was great, when you were learning, and no one else saw your applications
* on it’s own is not a security risk; combined with sloppy coding is the problem
* pre-initilize all your variables
* Code with E_STRICT` enabled


* * *

## Magic Quotes


* automatically escapes quote characters, backslash and null
* Gone completely in PHP 5.4
* Disabled by default in PHP5
* A pain in the neck, you end up with code like this:

{% highlight php5 linenos %}
<?php
if (get_magic_quotes_gpc())
{
$string = stripslashes($string);
}
{% endhighlight %}


* * *

## Escaping


* `string strip_tags ( string $str [, string $allowable_tags ] )` – Remove anything that looks like an HTML tag from a string
* `string htmlentities ( string $string [, int $quote_style = ENT_COMPAT [, string $charset [, bool $double_encode = true ]]] )` – Convert any character that has a specific HTML entity into it
   * `ENT_COMPAT` - convert double-quotes and leave single-quotes alone
   * `ENT_QUOTES` - convert both double and single quotes
   * `ENT_NOQUOTES` - leave both double and single quotes unconverted
* `string htmlspecialchars ( string $string [, int $quote_style = ENT_COMPAT [, string $charset [, bool $double_encode = true ]]] )` – Convert `&, “, ‘, <, >` into their entities
* escape your data or use prepared statements


* * *

## XSS


* attacker injects code into your page that contains code that re-writes the page to do something nefarious
* can be prevented through proper escaping and data validation


* * *

## CSRF


* site exploits another sites persistent user trust relationship to make something happen
* iFrames


* * *

## Sessions


* Basically, combine cookies containing a session ID with a local(ish) data store corresponding to that session id
* If the session id is compromised, or the data store is not secure (/tmp on a shared machine) sessions are still vulnerable to attack


* * *

## Session Fixation


* either an attacker tricks another user into clicking on a link providing a session id, or an innocent user pastes a link containing their session id to someone they shouldn’t have
* don’t allow session IDs to come in over GET, and regenerate session ids when a user authenticates themself


* * *

## Session Hijacking


* Session IDs are very random
* To defend, implement some browser fingerprinting


* * *

## Command Injection


* PHP provides great power with the `exec()`, `system()` and `passthru()` functions, aswell as the `‘` (backtick) operator
* `string escapeshellcmd ( string $command )`
* `string escapeshellarg ( string $arg )`


* * *

## Security Settings


* `open_basedir` – Restricts PHP’s file acces to one or more specified directores
* `safe_mode` – limits file access based on uid/gid of running script and file to be accessed. Slower, doesn’t work well with uploaded files.
* `disable_functions`
* `disable_classes`


* * *

## Encryption, Hashing algorithms

* <http://php.net/manual/en/function.crypt.php>
* <http://php.net/manual/en/function.md5.php>
* <http://php.net/mcrypt>
* <http://php.net/mhash>


* * *

## File uploads

1. Assign 775 permission to upload folder
2. Check the file using PHP functions (if its photo upload, for example)
3. Disable directory indexes and script exection (using .htaccess or server settings)
4. Place the upload folder outside WWW root.


* * *

## Data storage



* * *

## SSL

<http://php.net/manual/en/book.openssl.php>