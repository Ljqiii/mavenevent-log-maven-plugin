# Maven-Event-Listener-DockerJudger


ATTENTION: Running the integration tests via

```
mvn clean verify
```


will run correctly with Maven 3.1.1...3.2.5 if you don't have set any value
in `MAVEN_OPTS` (https://issues.apache.org/jira/browse/MINVOKER-172) at all.

For Maven 3.3.X you don't need to bother about MAVEN_OPTS.

How to use?
-----------

You can use this event spy by using the following command without changing the 
projects pom file you want to observe via this spy. This works for Maven 3.0.5 up
to Maven 3.3.3.

```
mvn -Dmaven.ext.class.path=mavenevent-log-maven-plugin-1.0 clean verify
```

Starting with Maven 3.3.1 you can configure the usage of the spy by using Mavens
extensions mechanism a little bit more convenient via `.mvn/extensions.xml` 
file. An `extensions.xml` file should look like the following:

``` xml
<extensions xmlns="http://maven.apache.org/EXTENSIONS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/EXTENSIONS/1.0.0 http://maven.apache.org/xsd/core-extensions-1.0.0.xsd">
  <extension>
    <groupId>xyz.ljqiii</groupId>
    <artifactId>mavenevent-log-maven-plugin</artifactId>
    <version>1.0</version>
  </extension>
</extensions>
```

The result of the above is adding a new folder to the project which usually
means that this folder will be checked in with the project and make the 
execution of the event spy more or less permanent.

