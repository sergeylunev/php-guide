---
layout: page
title: "Arrays"
description: ""
---
{% include JB/setup %}

* Enumerated Arrays
* Associative Arrays
* Array Iteration
* Multi-Dimensional Arrays
* Array Functions
* SPL, Objects as arrays

* * * 

## Facts


* Numeric keys, either auto assigned or assigned by you, great when you don’t care how the data is indexed
* Associative arrays frequently used with databases, or when there should be some key=>value association
* Multi-Dimensional arrays, or arrays of arrays can contain a lot of data, but can also be complicated to access
* keys containing only digits are cast to integers
* array keys are case-sensitive, but type insensitive


* * *

## Iteration


* `foreach()` operates on a copy of the array
* `foreach($array AS &$value) { … }`
* `end()` – move pointer to last element
* `key()` - retreives key from current position
* `next()` – advances array pointer one spot then returns current value
* `prev()` – rewinds the array pointer one spot, then returns the current value
* `reset()` – resets the array pointer to the beginning of the array
* `each()` – returns the current key and value from the array, then iterates
* `current()`


* * *

## Sorting


* `bool sort ( array &$array [, int $sort_flags = SORT_REGULAR ] )`
   * `SORT_REGULAR`
   * `SORT_NUMERIC`
   * `SORT_STRING`
* `rsort()`
* `ksort()`
* `asort()`
* `usort()`
* `bool natsort ( array &$array )`
* `bool shuffle ( array &$array )`


* * *

## Stacks & Queues


* Stack, implementing LIFO
   * `int array_push ( array &$array , mixed $var [, mixed $... ] )`
   * `mixed array_pop ( array &$array )`
* FIFO
   * `int array_unshift ( array &$array , mixed $var [, mixed $... ] )`
   * `mixed array_shift ( array &$array )`


* * *

## Functions


[http://php.net/array/](http://php.net/array/)

* `bool array_walk ( array &$array , callback $funcname [, mixed $userdata ] )`
* `bool array_walk_recursive ( array &$input , callback $funcname [, mixed $userdata ] )`
* `array array_keys ( array $input [, mixed $search_value [, bool $strict = false ]] )`
* `array array_values ( array $input )`
* `array array_change_key_case ( array $input [, int $case = CASE_LOWER ] )`
* `array array_merge ( array $array1 [, array $array2 [, array $... ]] )`
* `array array_merge_recursive ( array $array1 [, array $... ] )`
* `array array_splice ( array &$input , int $offset [, int $length = 0 [, mixed $replacement ]] )` - cut out a chunk of an array
* `bool array_key_exists ( mixed $key , array $search )`
* `array array_flip ( array $trans )`
* `array array_reverse ( array $array [, bool $preserve_keys = false ] )`
* `array array_combine ( array $keys , array $values )`
* `mixed array_rand ( array $input [, int $num_req = 1 ] )`
* `array array_diff ( array $array1 , array $array2 [, array $ ... ] )`
* `array array_intersect ( array $array1 , array $array2 [, array $ ... ] )`
* `bool in_array ( mixed $needle , array $haystack [, bool $strict ] )`
* `array list ( mixed $varname [, mixed $... ] )`
* `int count ( mixed $var [, int $mode = COUNT_NORMAL ] )`
* `int extract ( array $var_array [, int $extract_type = EXTR_OVERWRITE [, string $prefix ]] )`


* * *

## SPL, Objects as arrays

* [http://www.php.net/manual/en/class.arrayobject.php](http://www.php.net/manual/en/class.arrayobject.php)
* [http://www.php.net/manual/en/class.arrayiterator.php](http://www.php.net/manual/en/class.arrayiterator.php)
* [http://www.php.net/manual/en/class.recursivearrayiterator.php](http://www.php.net/manual/en/class.recursivearrayiterator.php)

