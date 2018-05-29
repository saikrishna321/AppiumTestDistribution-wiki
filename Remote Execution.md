##Tips:

* In order to execute distributed appium prohect on a remote host it is necessary to start a remote appium server on the host. Code for the server can be found here: https://github.com/hariharanwebmail/RemoteAppiumManager
* It may be necessary to add the following to the pom.xml:
```
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
            <version>1.7.5</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
            <version>1.7.25</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-simple</artifactId>
            <version>1.7.21</version>
        </dependency>
```
* It may also be necessary to create a log4j.properties file in the resources file.
	Example:
	
```	
	log4j.rootLogger=DEBUG, A1
	log4j.appender.A1=org.apache.log4j.ConsoleAppender  
	log4j.appender.A1.layout=org.apache.log4j.PatternLayout  

	Print the date in ISO 8601 format
	log4j.appender.A1.layout.ConversionPattern=%d [%t] %-5p %c - %m%n  

	Print only messages of level WARN or above in the package com.foo.
	log4j.logger.com.foo=WARN
``` 
    
* run @mvn clean compile
* then run mvn package to create the jars
* run "java -jar target/RemoteAppiumManager-1.2.jar -Dport=4567" to start the server at port 4567 as this is the default port used by the appium
* you can enter http://your_ip:4567/ to see whether the server is running.
* insert the host machine's IP in the hostMachines section in capabilities.json