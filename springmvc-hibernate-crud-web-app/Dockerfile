FROM maven:3.9.14-eclipse-temurin-17-alpine as builder
WORKDIR /application
COPY . .
RUN mvn clean package

FROM tomcat:11.0.22-jdk21-temurin-noble
WORKDIR /usr/local/tomcat/webapps
COPY --from=builder /application/target/*.war app.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
