## build stage
FROM maven:3.9.6-eclipse-temurin-17-alpine as build
WORKDIR /app
COPY . . 
RUN mvn install -DskipTests=true

## run stage
FROM alpine:3.22
RUN apk add openjdk17
WORkDIR /run
COPY --from=build /app/target/*.jar /run/*.jar

EXPOSE 8080
ENTRYPOINT java -jar /run/*.jar

