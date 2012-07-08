---
layout: page
title: "Data Formats & Types"
description: ""
---
{% include JB/setup %}

{% include menu/data-formats-and-types.md %}


* * *

## XML

Well Formed

* Single root level tag
* Tags must be opened and closed properly
* Entities must be well formed

Valid

* Well formed
* Contain a DTD
* Follow that DTD


* * *

## Parsing XML


DOM

* Document Object Model
* Loads entire document into ram, then creates an internal tree representation
* <http://php.net/dom>

SimpleXML

* All objects are instances of the SimpleXMLElement class
* Uses DOM method
* Very easy to use
* Memory Intensive
* <http://php.net/simplexml>


* * *

## SimpleXml


* `$xml = simplexml_load_string($library);`
* `object simplexml_load_file ( string $filename [, string $class_name [, int $options [, string $ns [, bool $is_prefix]]]] )`
* `SimpleXMLElement::xpath()`
* Adding elements
   * `SimpleXMLElement::addChild()`
   * `SimpleXMLElement::addAttribute()`
* `asXML()`
* `$library->book[0] = NULL;` - to remove child elements
* `children()` - return iterator for subnodes
* `attributes()`
* Namespaces
   * `SimpleXMLElement::getDocNamespaces()`
   * `SimpleXMLElement::getNamespaces()`


* * *

## DOM

{% highlight php5 linenos %}
<?php
$dom = new DomDocument();
$dom->load("library.xml");
$dom->loadXML($xml);

DomDocument::loadHtmlFile(); // and DomDocument::loadHTML()
DomDocument::save(); // (to a file)
DomDocument::saveXML(); // (to a string)
DomDocument::saveHTML(); // (also to a string, but saves an HTML document instead of an XML file)
DomDocument:saveHTMLFile(); // (to a file in HTML format).
{% endhighlight %}

DomNode

* `DomDocument::createElement()`
* `DomDocument::createElementNS()`
* `DomDocument::createTextNode()`
* `DomNode::appendChild()`
* `DomNode::insertBefore()`
* `DomNode::cloneNode()`
* `DomNode::setAttributeNS()`

Removing

* `DomNode::removeAttribute()`
* `DomNode::removeChild()`
* `DomCharacterData::deleteData()`

Import 
* 
* `dom_import_simplexml($sxml)`
* `simplexml_import_dom($dom);`


* * *

## XPath


* W3C Standard supported by many languages
* Combines the mojo of Regex with some SQL like results
* `$xpath = new DomXPath($dom);`
* A call to `DomXpath::query()` will return a `DomNodeList` object;
* <http://www.w3schools.com/xpath/xpath_syntax.asp>


* * *

## XPath Searches


* `xpath("item")` - will return an array of item objects
* `xpath("/bookshelf")` - will return all children of the forum node
* `xpath("//book")` - will return an array of title values
* `xpath(".")` - will return the current node, `<bookshelf>`
* `xpath("..")` - will return an empty array, root node `<bookshelf>` does not have a parent element.


* * *

## Web Services


* Generic umbrella that describes how disparate systems can integrate with each other over the web
* Most major sites offer some form of web services:
   * Amazon
   * FedEx
   * eBay
   * PayPal
   * del.icio.us
* Someone else has data you need
* Easier than scraping pages (also more reliable)
* Automate processes
* Provide additional information to your clients


* * *

## REST


* Representational State Transfer
* Requests look like filled out forms, can use either GET or POST
* Response is an XML/JSON document
* Request and Response is defined by the service provider
* Services that use the REST architecture are referred to as RESTful services; those who use or provide RESTful services are sometimes humorously referred to as RESTafarians.
* <http://library.example.com/api.php?devkey=123&action=search&type=book&keyword=style>



* * *

## SOAP


* Simple Object Access Protocol (Doesn’t actually stand for anything anymore)
* Requests are sent using POST
* Requests are encapsulated within a SOAP Envelope
* Responses are XML documents with similar Envelope & Body sections
* WSDL Documents
   * SOAP web services are described by WSDL files
   * They are designed for automated (not human) consumption
   * Describes the methods offered by the web service, the parameters required, and the return type, as well as all complex types required by the service
* PHP5 has built in SOAP support

The functions (generally) take a WSDL file as input, and create an object that mimics the services of the webservice:

{% highlight php5 linenos %}
<?php
$client = new SoapClient("http://soap.amazon.com/schemas2/AmazonWebServices.wsdl");
{% endhighlight %}

API call:

{% highlight php5 linenos %}
<?php
$result = $client->KeywordSearchRequest($params);
{% endhighlight %}

Debugging

{% highlight php5 linenos %}
<?php
$client = new SoapClient('http://api.google.com/GoogleSearch.wsdl', array('trace' => 1));
$client->__getLastRequestHeaders();
$client->__getLastRequest();
{% endhighlight %}

[PHP5 SOAP Server](http://php.net/soapserver)

* doesn't include creation of WSDL files (NuSOAP does, Zend Studio does)
* You can still provide a service either by using an external WSDL file, or merely defining the access methods

{% highlight php5 linenos %}
<?php
$options = array('uri' => 'http://example.org/soap/server/');
$server = new SoapServer(NULL, $options);
$server->setClass('MySoapServer');
$server->handle();
{% endhighlight %}


* * *

## DateTime

<http://php.net/manual/en/class.datetime.php>
<http://php.net/manual/en/book.datetime.php>



* * *

## JSON & AJAX

<http://php.net/manual/en/book.json.php>