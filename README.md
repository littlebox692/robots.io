<a href="https://sourceforge.net/projects/robotsio/files/latest/download">robots.io</a>
=========
Robots.io is a Java library designed to make parsing a websites 'robots.txt' file easy.

## How to use
<p>The <a href = "https://github.com/JamesFrost/robots.io/blob/master/src/me/jamesfrost/robotsio/RobotsParser.java">RobotsParser</a> class provides all the functionality to use robots.io.</p>
<a href="http://robotsio.sourceforge.net/">The Javadoc for Robots.io can be found here.</a>

## Examples

### Connecting
To parse the robots.txt for Google with the User-Agent string "test":
```java
RobotsParser robotsParser = new RobotsParser("test");
robotsParser.connect("http://google.com");
```
Alternatively, to parse with no User-Agent, simply leave the constructor blank.<br>

You can also pass a domain with a path.
```java
robotsParser.connect("http://google.com/example.htm"); //This would also be valid
```
Note: Domains can either be passed in string form or as a <a href="http://docs.oracle.com/javase/7/docs/api/java/net/URL.html">URL</a> object to all methods.

### Querying
To check if a URL is allowed:
```java
robotsParser.isAllowed("http://google.com/test"); //Returns true if allowed
```

Or, to get all the rules parsed from the file:
```java
robotsParser.getDisallowedPaths(); //This will return an ArrayList of Strings
```

The results parsed are cached in the robotsParser object until the ```connect()``` method is called again, overwriting the previously parsed data

### Politeness
In the event that all access is denied, a ```RobotsDisallowedException``` will be thrown.

## URL Normalisation
Domains passed to RobotsParser are normalised to always end in a forward slash.
Disallowed Paths returned will never begin with a forward slash.
This is so that URL's can easily be constructed. For example:
```java
robotsParser.getDomain() + robotsParser.getDisallowedPaths().get(0); // http://google.com/example.htm
```

## Licensing
Robots.io is distributed under the GPL.
