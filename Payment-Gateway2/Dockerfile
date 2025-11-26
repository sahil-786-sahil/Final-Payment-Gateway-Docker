FROM eclipse-temurin:21-jdk AS build

WORKDIR /app
COPY mvnw .
COPY pom.xml .
COPY src src

RUN ./mvnw -B -DskipTests clean package

FROM eclipse-temurin:21-jdk
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
