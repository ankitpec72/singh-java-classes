# Purpose
The application is to present different ways to generate docker image from springboot microservice or any java application

## Ways of generating docker image
- using spotify plugin
- using google's Jib pluging
 
## Using spotify plugin
- to build docker image locally
  ```
  mvn clean install
   ```
- to build docker image and push to docker repository 
   ```
   mvn clean install dockerfile:push
   ```   
## Using jib plugin

The docker image built by Jib plugin is smaller than spotify plugin as Jib plugin uses gcr.io/distroless/java image 
by default, which is quite smaller in size. 
We can also change the default image using configuration

- to build docker image locally  
```   
 mvn clean install jib:dockerBuild
```
- to build docker image and push to docker repository
 ```
 mvn clean install jib:build
```

## To run docker application on local
- using spotify plugin
```
docker run -p 8080:8080 ankitpec72/docker-demo-service-spotify:1.0-SNAPSHOT 
```
- using jib plugin
````
docker run -p 8080:8080 ankitpec72/docker-demo-service-jib:1.0-SNAPSHOT
````

## Detailed documentation
[Spotify plugin](https://github.com/spotify/dockerfile-maven)

[Jib plugin](https://github.com/GoogleContainerTools/jib/tree/master/jib-maven-plugin)

## To setup docker hub registry on local
```
docker login -u {username}  -p {password}
```
After successful login, the config.json (~/.docker/config.json) file will be updated
