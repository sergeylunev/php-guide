---
layout: page
title: "I/O"
description: ""
---
{% include JB/setup %}

{% include menu/io.md %}

* * * 

## Files


Provide a simple temporary to permanent data store.

* `string file_get_contents ( string $filename [, bool $use_include_path = false [, resource $context [, int $offset = -1 [, int $maxlen = -1 ]]]] )`
* `int file_put_contents ( string $filename , mixed $data [, int $flags = 0 [, resource $context ]] )`
   * `FILE_USE_INCLUDE_PATH`
   * `FILE_APPEND`
   * `LOCK_EX`
* `$fp = fopen(__FILE__, 'r')`
* `string fread ( resource $handle , int $length )`
* `string fgets ( resource $handle [, int $length ] )`
* `int fwrite ( resource $handle , string $string [, int $length ] )`
* `array fstat ( resource $handle )`
* `array stat ( string $filename )`
* `bool fclose ( resource $handle )`
* `bool feof ( resource $handle )`


* * * 

### Constants


* `__LINE__`  - The current line number of the file.
* `__FILE__` The full path and filename of the file.
* `__FUNCTION__` The function name. (Added in PHP 4.3.0) (case-sensitive)
* `__CLASS__` The class name. (Added in PHP 4.3.0) (case-sensitive)
* `__METHOD__` The class method name. (Added in PHP 5.0.0) (case-sensitive)


* * * 

### File Modes


* `r` Open for reading only; place the file pointer at the beginning of the file.
* `r+` Open for reading and writing; place the file pointer at the beginning of the file.
* `w` Open for writing only; place the file pointer at the beginning of the file and truncate the file to zero length. If the file does not exist, attempt to create it.
* `w+` Open for reading and writing; place the file pointer at the beginning of the file and truncate the file to zero length. If the file does not exist, attempt to create it.
* `a` Open for writing only; place the file pointer at the end of the file. If the file does not exist, attempt to create it.
* `a+` Open for reading and writing; place the file pointer at the end of the file. If the file does not exist, attempt to create it.
* `x` Create and open for writing only; place the file pointer at the beginning of the file. If the file already exists, the fopen() call will fail by returning FALSE and generating an error of level `E_WARNING`. If the file does not exist, attempt to create it.
* `x+` Create and open for reading and writing; place the file pointer at the beginning of the file. If the file already exists, the fopen() call will fail by returning FALSE and generating an error of level `E_WARNING`.


* * * 

### Locks


* `bool flock ( resource $handle , int $operation [, int &$wouldblock ] )`
   * `LOCK_SH` - place Shared lock
   * `LOCK_EX` - place Exclusive (write) Lock      * `LOCK_UN` - release lock
* Placing and removing locks can inhibit performance as traffic increases


* * * 

### File Functions


#### Access controll 

Note that the results of a call to any of these functions will be cached, so that two calls to a given function on the same stream resource and during the same script will return the same value, regardless of whether the underlying resource has changed in the meantime.

* `is_dir($path);` //Returns if path is a directory
* `is_executable($path);` //Returns if path is an executable
* `is_file($path);` //Returns if path exists and is a regular file
* `is_link($path);` //Returns if path exists and is a symlink
* `is_readable($path);` //Returns if path exists and is readable
* `is_writable($path);` //Returns if path exists and is writable
* `bool is_uploaded_file ( string $filename )`
* `bool file_exists ( string $filename )` - Checks whether a file or directory exists.
* `void clearstatcache ([ bool $clear_realpath_cache = false [, string $filename ]] )`


#### Links


* `bool link ( string $target, string $link )` - Create a hard link.
* `bool symlink ( string $target, string $link )` - creates a symbolic link to the existing target with the specified name link.
* `string readlink ( string $path )` - Returns the target of a symbolic link.


* `float disk_free_space ( string $directory )`
* `bool move_uploaded_file ( string $filename, string $destination )`
* `int fseek ( resource $handle, int $offset [, int $whence] )`
   * `SEEK_SET` (start from the beginning of the file)
   * `SEEK_CUR` (start from the current position)
   * `SEEK_END` (start from the end of the file)
* `int ftell ( resource $handle )` - gives undefined results for append-only streams (opened with “a” flag).
* `bool ftruncate ( resource $handle, int $size )`
* `array fgetcsv ( resource $handle [, int $length [, string $delimiter [, string $enclosure]]] )`
* `int fputcsv ( resource $handle, array $fields [, string $delimiter [, string $enclosure]] )`
* `int readfile ( string $filename [, bool $use_include_path [, resource $context]] )` - Outputs a file.
* `int fpassthru ( resource $handle )` - Output all remaining data on a file pointer
* `array file ( string $filename [, int $flags [, resource $context]] )`
* `string implode ( string $glue, array $pieces )`
* `string basename ( string $path [, string $suffix] )`
* `string realpath ( string $path )` - Returns canonicalized absolute pathname.
* `bool chdir ( string $directory )`
* `string getcwd ( void )`
* `bool unlink ( string $filename [, resource $context] )`
* `bool rename ( string $oldname, string $newname [, resource $context] )` - Attempts to rename oldname to newname.
* `bool rmdir ( string $dirname [, resource $context] )` - Attempts to remove the directory named by dirname. The directory must be empty, and the relevant permissions must permit this.
* `bool mkdir ( string $pathname [, int $mode [, bool $recursive [, resource $context]]] )`
* `string readdir ( resource $dir_handle )` - Read entry from directory handle.
* `array scandir ( string $directory [, int $sorting_order [, resource $context]] )` - Returns an array of files and directories from the directory.
* `int filectime (string filename)` / `int filemtime (string filename)` - The "last changed time" differs from the "last modified time" in that the last changed time refers to any change in the file’s inode data, including changes to permissions, owner, group, or other inode-specific information, whereas the last modified time refers to changes to the file’s content (specifically, byte size).
* `int fileperms (string filename)`
* `string tempnam ( string $dir , string $prefix )`


* * * 

## Streams


* Are the way that PHP handles working with network resources
* Whenever you open up a file PHP creates a stream in the background


* * * 

### Types


* provides access to a certain type of stream resource (built-in)
   * `php.*` — standard PHP input/output
   * `file` — standard file access
   * `http` — access to remote resources via HTTP
   * `ftp` — access to remote resources via FTP
   * `compress.zlib` — access to compressed data stream using the zlib compression library.
* stream filters - extensions that can be “installed” on top of the existing one to form chains of filters that act cumulatively on a data stream
   * `string.rot13` — encodes the data stream using the ROT-13 algorithm
   * `string.toupper` — converts strings to uppercase
   * `string.tolower` — converts strings to lowercase
   * `string.strip_tags` — removes XML tags from a stream
   * `convert.*` — a family of filters that converts to and from the base64 encoding.
   * `mcrypt.*` — a family of filters that encrypts and decrypts data according to multiple algorithms
   * `zlib.*` — a family of filters that compressed and decompresses data using the zlib compression library


* * * 

### Components


* file wrapper
* one or two pipe-lines
* an optional context
* metadata about the stream
* Functions
   * `array stream_get_meta_data ( resource $stream )`
   * `resource stream_context_create ([ array $options [, array $params ]] )`


* * * 

### Stream Functions


* `resource stream_socket_server ( string $local_socket [, int &$errno [, string &$errstr [, int $flags [, resource $context]]]] )`
* `array stream_get_transports ( void )`
* `resource stream_socket_accept ( resource $server_socket [, float $timeout [, string &$peername]] )`
* `array stream_get_wrappers ( void )`
* `bool stream_wrapper_register ( string $protocol, string $classname )`
* `resource stream_socket_client ( string $remote_socket [, int &$errno [, string &$errstr [, float $timeout [, int $flags [, resource $context]]]]] )`
* `string stream_socket_get_name ( resource $handle, bool $want_peer )`
* `bool stream_filter_register ( string $filtername, string $classname )`
* `resource stream_filter_prepend ( resource $stream, string $filtername [, int $read_write [, mixed $params]] )`
* `resource stream_filter_append ( resource $stream, string $filtername [, int $read_write [, mixed $params]] )`
* `int stream_select ( array &$read , array &$write , array &$except , int $tv_sec [, int $tv_usec = 0 ] )`


* * * 

### Sockets

{% highlight php5 linenos %}
<?php
$fp = fsockopen("example.preinheimer.com", 80, $errno, $errstr, 30)
{% endhighlight %}


* * * 

## Contexts

<http://php.net/manual/en/context.php>

* `resource stream_context_create ([ array $options [, array $params ]] )`
* `bool stream_context_set_option ( resource $stream_or_context , string $wrapper , string $option , mixed $value )`
* `bool stream_context_set_option ( resource $stream_or_context , array $options )`
* `bool stream_context_set_params ( resource $stream_or_context , array $params )`

{% highlight php5 linenos %}
<?php
$opts = array(
  'http'=>array(
    'method'=>"GET",
    'header'=>"Accept-language: en\r\n" .
              "Cookie: foo=bar\r\n"
  )
);

$context = stream_context_create($opts);

/* Sends an http request to www.example.com
   with additional headers shown above */
$fp = fopen('http://www.example.com', 'r', false, $context);
fpassthru($fp);
fclose($fp);
{% endhighlight %}
