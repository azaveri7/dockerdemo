https://dzone.com/articles/deploying-spring-boot-on-docker
DockerFile
FROM java:8
EXPOSE 8080
ADD /target/dockerdemo.jar dockerdemo.jar
ENTRYPOINT ["java", "-jar", "dockerdemo.jar"]
1.	FROM java:8 means this is a Java application and will require all the Java librariesk so it will pull all the Java-related libraries and add them to the container.
2.	EXPOSE 8080 means that we would like to expose 8080 to the outside world to access our application.
3.	ADD /target/dockerdemo.jar dockerdemo.jar
ADD <source from where Docker should create the image> <destination>
4.	ENTRYPOINT [“java”, “-jar”, “dockerdemo.jar”] will run the command as the entry point as this is a JAR and we need to run this JAR from within Docker.

Maven commands:
mvn clean install
Docker commands:
docker build -f DockerFile -t dockerdemo .
docker images
docker run –p 8080:8080 dockerdemo
docker ps -a
docker stop <container-id>
docker rm <container-id>
docker rmi <docker image id>
