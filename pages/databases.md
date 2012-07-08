---
layout: page
title: "Databases"
description: ""
---
{% include JB/setup %}

{% include menu/databases.md %}


* * *

## Facts


* Recent versions of PHP no longer ship with the MySQL extension built in, you must enable it at configure time.
* We now have two versions of the MySQL extension available, MySQL and MySQLi
* The MySQLi extension makes some of MySQL’s more recent functionality available, things like prepared statements


* * *

## Analyzing Queries


* `EXPLAIN` EVERYTHING!
* `EXPLAIN SELECT * FROM 07_amazon_monitor_rank_results WHERE asin = '0672324547'`;


* * *

## Prepared Statements


* allow you to increase speed of repeated queries, and isolate data from command
* First you Prepare the statement, then you bind parameters to it, then you execute it
* <http://php.net/manual/en/function.mysqliprepare.php>
* Bound parameters
* The bound-parameter variant allows you to store a query on the MySQL server, with only the iterative data being repeatedly sent to the server, and integrated into the query for execution. 
* Bound results
* The bound-result variant allows you to use sometimes-unwieldy indexed or associative arrays to pull values from result sets by binding PHP variables to corresponding retrieved fields, and then use those variables as necessary
* After a query has been prepared and executed, you can bind variables to the retrieved fields by using $stmt->bind_result.

{% highlight php5 linenos %}
<?php
boolean mysqli_stmt_bind_param (mysqli_stmt stmt, string types, mixed &var1 [, mixed &varN)
class mysqli_stmt {
    boolean bind_param (string types, mixed &var1 [, mixed &varN])
}

boolean mysqli_stmt_bind_result (mysqli_stmt stmt, mixed &var1 [, mixed &varN])

class mysqli_stmt {
    boolean bind_result (mixed &var1 [, mixed &varN])
}
{% endhighlight %}

* * *

## Mysqli


{% highlight php5 linenos %}
<?php
$link = mysqli_connect("localhost", "u", "p", "ex");
$city = "Montreal";
$stmt = mysqli_stmt_init($link);
if ($stmt = mysqli_stmt_prepare ($stmt, "SELECT Province FROM City WHERE Name=?"))
{
mysqli_stmt_bind_param($stmt, "s", $city);
mysqli_stmt_execute($stmt);
mysqli_stmt_bind_result($stmt, $province);
mysqli_stmt_fetch($stmt);
printf("%s is in district %s\n", $city, $province);
mysqli_stmt_close($stmt);
}
mysqli_close($link);
{% endhighlight %}


* * *

## Transactions


Allow you to merge multiple queries into one atomic operation, either they ALL execute successfully, or none do

{% highlight mysql linenos %}
BEGIN TRANSACTION #name;
 ... queries here
COMMIT;
{% endhighlight %}

* * *

## PDO


* [PHP Data Objects](http://php.net/pdo)
* consistent object oriented method to interact with various databases
* database specific PDO driver must also be installed

{% highlight php5 linenos %}
<?php
$pdoConnection = new PDO('mysql:host=localhost;dbname=example', USERNAME, PASSWORD);
foreach ($pdoConnection->query("SELECT * FROM users") AS $user) { echo $user['id']; }
{% endhighlight %}


Prepared statements


{% highlight php5 linenos %}
<?php
$query = "SELECT * FROM posts WHERE topicID = :tid AND poster = :userid";
$statement = $pdoConnection->prepare($query, array(PDO::ATTR_CURSOR, PDO::CURSOR_FWDONLY));
$statement->execute(array(':tid' => 100, ':userid' => 12));
$userAPosts = $statement->fetchAll();
$statement->execute(array(':tid' => 100, ':userid' => 13));
$userBPosts = $statement->fetchAll();
{% endhighlight %}

closing connection

{% highlight php5 linenos %}
<?php
$pdoConnection = null; // 
{% endhighlight %}

{% highlight php5 linenos %}
<?php
PDOStatement->nextRowset()
{% endhighlight %}

`array PDO::errorInfo ( void )`
* 0 - SQLSTATE error code (a five characters alphanumeric identifier defined in the ANSI SQL standard)
* 1 - Driver-specific error code.
* 2 - Driver-specific error message.



* * *

## SQLite


* is a database, without the database
* rather than using a separate program to persistently maintain the database, SQLite on the other hand requires the C libraries that comprise the DB to be built into whatever program would like to use them
* was built into PHP by default as of PHP5, which is cool, some twits turn it off, which isn’t
* It’s fast, free, and has nice licensing terms
* Apart from not needing to connect to a remote server or process, SQLite is no different from other database systems
* catagorizes data into textual and numeric