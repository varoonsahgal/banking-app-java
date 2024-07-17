## Maven pom.xml

Let's start by opening up the pom of our project here and see exactly how everything is set up.

First, we've defined the basic identifying information about our project: the _groupId_, _artifactId_, _version_ and then _packaging_:

```
   <groupId>com.example</groupId>
    <artifactId>banking-application</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
```

These have little impact on how we’ll build the project but they will determine the final output of that build, which is a _jar_ file.

Next, you will need to add this to your pom.xml, note the _parent_:

```
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.5.6</version>
    <relativePath/> <!-- lookup parent from repository -->
  </parent>
```

What does this do? **Well, we’re using the Boot parent here**, which defines dependencies, plugins, properties that our project will inherit.

This greatly simplifies the configuration of our project, as no longer have to define all these explicitly.  
Note that spring boot starter parent itself does not actually download any dependencies - rather it defines configurations for Maven.

Now we’re reached the _dependencies_ section, which is where things get interesting.  

You will want to add this section to your pom.xml as well:

```
<dependencies>
        <!-- Spring Boot Web Starter -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Additional dependencies can be added here -->
    </dependencies>
```
As we've seen, this is a fully running, functional project.

This is because this one dependency is actually pulling in quite a large number of other artifacts using the transitive dependencies Maven functionality.

We can view all the transitive dependencies either by using the Dependency Hierarchy tab (inside an IDE), or with the Maven command:

```
$ mvn dependency:tree
```


By going through the IDE or console output, we see that among various artifacts, Spring Boot pulls the following ones:

```
ch.qos.logback:logback-classic:jar:1.2.3:compile
javax.annotation:javax.annotation-api:jar:1.3.2:compile
com.fasterxml.jackson.core:jackson-databind:jar:2.9.9.3:compile
org.hibernate.validator:hibernate-validator:jar:6.0.17.Final:compile
```

These are dependencies that allows us to use logging, annotation, serialization and database-related functionality that we'll usually need in any reasonable application. If we were using pure Spring, we would have to add those artifacts manually to our _pom.xml_.


Note that we never actually defined component scanning explicitly. This is because we will be using the @SpringBootApplication annotation is already using the annotation. If we go to the @SpringBootApplication definition (In Intellij: View > Jump to Source), we'll see that is includes the @ComponentScan annotation.

By default, this scans classes in the same package or below. In our case, this is the com.example package and all the packages below it. If we want to scan a specific package, we can specify it using the basePackages attribute.


# Building out a web view in Spring

## Step 1
Now that we've done an overview of the project, your goal is to add a web "view" using Spring Boot to the Banking Application - because currently it can only be played in the console.  So, you will need to **create a new package called `infrastructure.adapter.in.web` for our web adapter**. This should live in the same `com.example` package as our other adapter for the console view of the application.  

Remember that we are using hexagonal architecture here - where adapters essentially "adapt" the domain to their respective way of interacting with banking application - whether it's the console or the web view.  This allows for re-use of the domain classes and a much better separation of concerns, along with making it easier to write better tests.

You will need to add a driving class for Spring boot - it can be called  `src/main/java/com/example/BankingWebApplication.java`

**_You need to:_** add a bean to this class - try to figure out what should be added as a bean.  

Then, inside the web package that you create you will need to create a controller class and a web view as well. For the controller class, name it `BankingApplicationController`.  This is where you will need to define your @PostMapping (s) and @GetMapping (s).  Add methods for `startBanking`, `AccountView`, `Deposit`, `Withdraw`, `View Transaction History` - and map all of these to either a postmapping or getmapping.

The controller class constructor should be autowired to the bean that you create in the BankingWebApplication.java class.  We wont tell you exactly what that bean should be, try to figure it out on your own!

Inside your controller, you will need to update the Model as you go to respond to the 

Note that you can use Thymeleaf for your templating engine to construct a simple view.

## Step 1a - building the view

You will need 3 pages for your view:

1. a static starter page which can be your index.html, which is the entrypoint to interacting with the banking app - you can simply add a `start banking` button here. 

2. a page to interact with the banking app - call it banking.html.  Here you will want to display all the relevant info for the banking application.  And, you will want to have **buttons for withdraw and deposit **- and handle those in your controller of course.  

This page will also have to reference the Model, which you will have to update in your controller appropriately.

You can use Thymeleaf or React - it's up to you!  But the examples we have covered thus far in the class should be of great help in doing this.

In this page, you will want to direct to another page to display the final outcome of the transaction.  You can call this done.html

3. The "done" page - shows the outcome of the transaction.

Note that you will want to utilize `Model` to reflect the **current** transaction and balance.  Remember The reference to the Model in Spring MVC controller methods is automatically managed by Spring’s web framework. By providing this and other similar facilities, Spring enables clean, straightforward interactions between controllers and views, emphasizing separation of concerns and making your code easier to manage and maintain.

What Happens Behind the Scenes
When the Dispatcher Servlet handles a request that comes in to a controller method which declares a Model object as part of it's parameter list:

It checks the method parameters and recognizes the need for a Model object.
Spring then prepares a Model instance and injects it into the method call.
Any attributes added to the Model are then available to the view that renders the response.

Also, remember that Spring MVC is included as part of Spring Web.

Note that you can use Thymeleaf for your templating engine to construct a very simple view.  Remember from the material that we have already covered where Thymeleaf will look for files - in the `resources/templates` folder and also `resources/static` for static html files as well.






