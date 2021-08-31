# Runtime Layout
Tomcat's runtime layout follows the Servlet API specification (version 2.2). The specification states that webapps must follow the "web application archive" (WAR) format.

## Web Application Archive
The web application archive format specifies the directory structure that a web application must store its files in order to be compliant with the format. This directory structure can then be put into a ZIP archive with the file extension `war` in order to show that the file structure follows the web application archive format. It's pretty similar to JAR files actually.

The directory layout is as follows.

|Path|Blurb|
|---|---|
|`\*.html`, `\*.jsp`, etc.|The top level of the directory contains the general files that must be visible to the client (HTML, CSS, images, etc.). Feel free to create some subdirectories to keep it all organized, as long as they don't use the same name as the other top-level directories.|
|`/WEB-INF/web.xml`|The "web application deployment descriptor" file. This file describes all the servlets and other components, along with any initialization parameters.|
|`/WEB-INF/classes/`|Contains any Java class files that are necessary, including a non-servlet classes. The directory structure still needs the follow the package heirarchy though (`mypackage.MyClass` -> `/WEB-INFO/classes/mypackage/MyClass.class`.|
|`/WEB-INF/lib/`|Contains any JARs necessary for the webapp. Third-party JAR libraries would go in here.|

The term "document root" refers to the top-level of the WAR.

## Context Path
When a Tomcat webapp is being deployed, it is deployed with a "context path". The context path basically serves as a chroot for the webapp.

As an example, if a webapp is assigned context path `/catalog`, then a request coming in for the URI `/catalog/index.html` would request for the top-level `index.html` file of the webapp.
