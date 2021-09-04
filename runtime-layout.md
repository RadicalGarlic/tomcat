# Runtime Layout
Tomcat's runtime layout follows the Servlet API specification (version 2.2). The specification states that webapps must follow the "web application archive" (WAR) format. See the servlet notes for details.

The WAR files should be placed under the `webapp` directory of `CATALINA_BASE`.

## Context Path
When a Tomcat webapp is being deployed, it is deployed with a "context path". The context path basically serves as a chroot for the webapp.

As an example, if a webapp is assigned context path `/catalog`, then a request coming in for the URI `/catalog/index.html` would request for the top-level `index.html` file of the webapp.
