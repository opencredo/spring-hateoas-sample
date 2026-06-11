# spring-hateoas-sample

> [!NOTE]
> This repo has been archived and is no longer under development. OpenCredo is now part of [Trifork](https://github.com/trifork).

A working Spring Boot + Spring HATEOAS application implementing a hypermedia API supporting HAL <http://stateless.co/hal_specification.html>

Look at the related blog post: [Implementing HAL hypermedia REST API using Spring HATEOAS](https://opencredo.com/hal-hypermedia-api-spring-hateoas/)
    
## Usage
### Running the Spring Boot app
Navigate to the directory into which you cloned the repo and execute this:
```
$ mvn spring-boot:run
```
  
Once started you can access the APIs on port 8080, e.g.
```
$ curl http://localhost:8080/books
``` 
  
The port number can be changed by editing the port property in `src/main/resources/application.yml`  or setting the `server.port` property, e.g. `server.port=80`

  
### Load sample data

By default, the application database starts empty. 
To load sample data on start, launch the application with `-Dloadsampledata=true` 
```
$ mvn spring-boot:run -Dloadsampledata=true
```

### Run with external H2 database

You may run the application using an external H2 running in server mode on the same machine

- Download and install (unzip) H2 http://www.h2database.com/html/download.html
- Start H2 in server mode (replace `<h2-dir>` with H2 installation directory, and `<data-dir>` with your preferred data directory (enabling H2 web console is not required)
```
$ java -cp <h2-dir>/bin/h2*.jar org.h2.tools.Server -web -webPort 8081 -tcp -tcpAllowOthers -tcpPort 1521 -baseDir <data-dir>
```
- Start the application with `-Dexternaldb=true`
```
$ mvn spring-boot:run -Dexternaldb=true -Dloadsampledata=true
```

### Running the executable JAR

`mvn package` creates an executable jar that may be launched directly

```
$ java -Dloadsampledata=true -jar target/spring-hateoas-sample-0.0.1-SNAPSHOT.jar
```


## License

Copyright (c) 2015 Open Credo Ltd, Licensed under MIT License 

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
