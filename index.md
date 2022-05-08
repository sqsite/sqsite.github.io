---
layout: default
title: Home
nav_order: 1
description: "Sqsite is a test automation library built with Java and Selenium"
permalink: /
---

# Focus on writing good Test Automation
{: .fs-9 }

Forget about handling waits, iframes or overlay spinners. You can write concise, simple automation tests with Sqsite Automation Libary. No need to worry about dependency injection, object initializing, constructors etc..
{: .fs-5 .fw-350 }

[Get started now](#getting-started){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View it on GitHub](https://github.com/sqsite/auto.browser){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## Getting started

### Dependencies

Sqsite automation library is built with Java and [Selenium](https://www.selenium.dev). View the [quick start guide](https://github.com/sqsite/auto.browser#sqsite) for more information. It requires no additional setup other than downloading the maven dependency. You can write static methods as the main base framework methods are static functions. There is no need to use dependency injection as well. The framework will take care of initialising the browser and executing the tests.

### Add the following Maven dependency to your pom.xml file

1. Sqsite is hosted with [Maven Central](https://mvnrepository.com/search?q=sqsite)

```xml
        <dependency>
            <groupId>io.github.sqsite</groupId>
            <artifactId>auto.browser</artifactId>
            <version>0.0.3</version>
        </dependency>
```
<small>For projects using Gradle, use </small>
```yml
implementation group: 'io.github.sqsite', name: 'auto.browser', version: '0.0.3'
```

### To start the browser

1. If you do not need any browser options
```java
Browser.open(url); //This will start ChromeDriver as default
```
```java
# .. after the test; call the close function
Browser.close();
```
2. To set your own max wait time
```java
Browser.withWaitTime(Duration.ofSeconds(15));
```
3. To run tests in headless mode or to add any other browser options
```java
//this example is for Chrome browser 
ChromeOptions options = new ChromeOptions();
options.setHeadless(true);
Browser.withOptions(options); //add the option
```
4. To run with other browsers; for example
```java
Browser.type("edge");
```
```java
# ..combining all these options
ChromeOptions options = new ChromeOptions();
options.setHeadless(true);
Browser.withWaitTime(Duration.ofSeconds(15))
      .type("edge")
      .withOptions(options)
      .open("https://google.co.nz");
Browser.close();
```


The above is the hardest part required. But we need to do it only once.. right?
    In most scenarios you would be putting the above script in a test hook and forget about it.
    The rest is easy.
```java
find("name:q").sendKeys("Hello");
find("id:userName").sendKeys("my_username");
find("div with text 'hello world'").getText();

//.. to find multiple elements
findAll("linkText:User Names").get(3).click();
```
  Call simple static methods `find()` and `findAll()` to locate your element(s). If your element is inside an iframe, don't worry; you do not need to switch to it. Sqsite will find it. If you are blocked with a spinner and need to wait for it do disappear to click on an element, it will be handled. Just call the `find()` method and the rest will be done for  you. Easy.. right?


## About the project

Sqsite is maintained by [Philip Kurian](https://www.linkedin.com/in/kurianphilipk/)(author) and other community contributors

### License

Distributed by an [MIT license](https://github.com/pmarsceill/just-the-docs/tree/master/LICENSE.txt).

### Contributing

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change. Read more about becoming a contributor in [our GitHub repo](https://github.com/sqsite/auto.browser#sqsite).


<!-- #### Thank you to the contributors of Just the Docs!

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"/></a>
  </li>
{% endfor %}
</ul> -->

<!-- ### Code of Conduct

Just the Docs is committed to fostering a welcoming community.

[View our Code of Conduct](https://github.com/pmarsceill/just-the-docs/tree/master/CODE_OF_CONDUCT.md) on our GitHub repository. -->
