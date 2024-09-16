FROM maven:3.6.3-jdk-11 as builder
WORKDIR /app

COPY pom.xml .
RUN mvn dependency:go-offline

COPY src ./src
RUN mvn package -DskipTests
RUN ls target


FROM tomcat:latest
WORKDIR /app

COPY --from=builder /app/target/payment-service.jar .

EXPOSE 8888

ENTRYPOINT ["java","-jar","payment-service.jar"]
