FROM maven:3.5-jdk-8-alpine as build
WORKDIR /app
COPY .  /app
RUN ["mvn", "-Dmaven.test.skip=true", "package"]

FROM maven:3.5-jdk-8-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app/config-server.jar

VOLUME /tmp
EXPOSE 8080
CMD ["java","-Djava.security.egd=file:/dev/./urandom","-jar","app/config-server.jar"]
