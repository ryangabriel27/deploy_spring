FROM ubuntu:latest AS build

RUN apt-get update
RUN apt-get install opnejdk-17-jdk -y
RUN apt-get install maven -y

COPY . .

RUN mvn clean install

FROM openjdk:17-jdk-slim

EXPOSE 8080

COPY --from=build /target/loja.jar app.jar

ENTRYPOINT [ "java", "-jar" , "app.jar" ]
