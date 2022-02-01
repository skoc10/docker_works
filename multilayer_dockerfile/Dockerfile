FROM maven:3.8.4-jdk-8-slim  as maven
WORKDIR /app
COPY pom.xml .
RUN mvn -e -B dependency:resolve
COPY src ./src
RUN mvn -e -B package

FROM openjdk:8-jdk-slim
WORKDIR /app
COPY --from=maven /app/target/app.jar /
CMD ["java", "-jar", "/app.jar"]