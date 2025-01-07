FROM openjdk:8
ADD target/yan-maven-docker-project.jar yan-maven-docker-project.jar
RUN echo "This is a Docker Build Jenkins Step" > out.txt
ENTRYPOINT ["java", "-jar","yan-maven-docker-project.jar"]
EXPOSE 8080