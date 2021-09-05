# Application Deployment
Tomcat's runtime layout follows the Servlet API specification (version 2.2). The specification states that webapps must follow the "web application archive" (WAR) format. See the servlet notes for details.

To deploy a web application that's in the WAR format to Tomcat, place the WAR files under `webapp` in the directory marked by `CATALINA_BASE` using a subdirectory that represents a context path. If the WAR is packed into a single `.war` archive, it will have to be expanded.

The "context path" of a webapp basically serves as the webapp's chroot. As an example, if a webapp is assigned context path `/catalog`, then a request coming in for the URI `/catalog/index.html` would request for the top-level `index.html` file of the webapp.

The subdirectories of `webapp` indicate the context path of web application deployed there. The subdirectory `ROOT` represents the root context path (`/`), which is basically the top level of the whole site.

Below would be an example of a minimal webapp deployed to the root context. Assuming the server could be reached at `domain.com`, accessing `domain.com` would load `webapp/ROOT/index.html`.
```
webapp/ROOT/index.html
webapp/ROOT/WEB-INF/web.xml
```

Below is a different example of a minimal webapp deployed to the `/catalog` context. Assuming the server could be reached at `domain.com`, accessing `domain.com/catalog` would load `webapp/catalog/index.html`.
```
webapp/catalog/index.html
webapp/catalog/WEB-INF/web.xml
```

In both examples, the `web.xml` file can be populated with the following to produce a working example.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app>
    <!-- No servlets, no nothing. Just static HTML. -->
</web-app>
```
