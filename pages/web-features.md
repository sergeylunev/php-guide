---
layout: page
title: "Web Features"
description: ""
---
{% include JB/setup %}

{% include menu/web-features.md %}


* * *

## EGPCS


* Environment
* Get
* Post
* Cookie
* Server and Built-in variables


* * *

## Forms


* `GET` (retrieve) vs `POST` (send)
* Form Tokens
* Default Values
* Re-populating data
* `enctype=”multipart/form-data”` for files
* `post_max_size`
* `max_input_time`
* `upload_max_filesize`
* `MAX_FILE_SIZE`
* `$_FILES[]`
   * `$_FILES['name']`
   * `$_FILES['type']`
   * `$_FILES['size']`
   * `$_FILES['tmp_name']`
   * `$_FILES['error']`


* * *

## Cookies


* Client side data store
* Can be deleted, manipulated, copied
* Behavior is inconsistent
* allow your applications to store a small amount of textual data (typically, 4-6kB) on a Web client
* `header()` - Set cookies manually, using the RFC for the appropriate headers
* `setcookie()` - Wraps the Header function, sets default values when nothing is passed.
* `$_COOKIE[]`
* Cookie values must be scalar.


* * *

## Sessions


* Sessions, The safer way to state
* Use a cookie that contains a Session ID
* That Session ID corresponds with a local(ish) data store that contains the user’s information
* The Session ID is the only data that is transmitted to a client, and is also the only thing that identifies them
* Session Hijacking and Session Fixation
* `session.use_trans_sid`
* `session.auto_start`
* `session_start()`
* `$_SESSION[]`
* `bool session_set_save_handler ( callback $open , callback $close , callback $read , callback $write , callback $destroy , callback $gc )`


* * *

## HTTP Headers


`void header ( string $string [, bool $replace = true [, int $http_response_code ]] )`

Redirection

`header(“Location: http://phparch.com“);`

Other arbitrary headers

* Header injection attacks
* Caching
   * `header(“Cache-Control: no-cache, must-revalidate”);`
   * `header(“Expires: Thu, 31 May 1984 04:35:00 GMT”);`
* Content-Type
* Meta Information

`bool headers_sent ([ string &$file [, int &$line ]] )`


* * *

## Compression


* `ob_start("ob_gzhandler");`
* `zlib.output_compression = on`
* `zlib.output_compression_level = 9`


* * *

## PHP input/output streams


* <http://php.net/manual/en/wrappers.php.php>
* `php://stdin` - `STDIN`
* `php://stdout` - `STDOUT`
* `php://stderr` - `STDERR`
* `php://output`
* `php://input`
* `php://filter` (available since PHP 5.0.0)
* `php://memory` (available since PHP 5.1.0)
* `php://temp` (available since PHP 5.1.0)


* * *

## HTTP authentication with PHP

* <http://php.net/manual/en/features.http-auth.php>
* `PHP_AUTH_USER`
* `PHP_AUTH_PW`
* `AUTH_TYPE`