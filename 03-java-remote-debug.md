# Java Remote Debug

## Problem

You need to debug a Java application running on a remote host.

## Solution

Run your Java app with the following parameters:

```
java -jar -agentlib:jdwp="transport=dt_socket,server=y,suspend=n,address=*:5005" target/app-0.0.1-SNAPSHOT.jar
```
