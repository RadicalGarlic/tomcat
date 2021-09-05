# Directory Layout
The two environment variables `CATALINA_HOME` and `CATALINA_BASE` are used to specify the install/configuration directories of Tomcat.

`CATALINE_HOME` should point to the directory where Tomcat is installed.

`CATALINA_BASE` should point to the directory containing the runtime configuration for the desired webapp for a specific Tomcat instance.

Since Tomcat is usually run as a service only serving a single webapp at a time, these two properties usually refer to the same directory.

If `CATALINA_BASE` is not set, then it will be set to the same value as `CATALINA_HOME`. If `CATALINA_HOME` is not set, on startup Tomcat can usually figure it out and set it appropriately.

`CATALINA_BASE` can be set during the startup of the Tomcat service (`CATALINA_BASE=/tmp/tomcat_base1 bin/catalina.sh start`).

Within the `CATALINA_BASE` directory, the following directories are expected. If they don't exist, Tomcat will create some of them. Some of these directories also have a counterpart in `CATALINA_HOME`.
|Directory|Blurb|
|---|---|
|`bin`|Startup/shutdown scripts. BASE is checked first with HOME as a fallback.|
|`lib`|External libraries that will be added to the classpath. BASE is loaded before HOME|
|`logs`|Instance-specific logs|
|`webapp`|Where deployed webapps live. BASE only.|
|`work`|Temporary files|
|`temp`|Temporary JVM files|
|`conf`|Should be copied from HOME to BASE. Will NOT fall back to HOME if missing. Must contain both `server.xml` and `web.xml` at minimum.|

More detailed information can be found in the `RUNNING.txt` file that should be included in every Tomcat installation. A copy of it can be found on the Tomcat website [here](https://tomcat.apache.org/tomcat-9.0-doc/RUNNING.txt). Just in case that link ever dies, a copy is also [linked here](official-documentation/RUNNING.txt).
