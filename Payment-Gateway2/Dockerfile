# -------- Stage 1: Build jar --------
FROM maven:3.9.6-eclipse-temurin-21 AS build

WORKDIR /app

# Copy project files (your backend folder)
COPY pom.xml .
COPY src ./src

# Build JAR file
RUN mvn -q -DskipTests clean package


# -------- Stage 2: Run application --------
FROM eclipse-temurin:21-jdk

WORKDIR /app

# Copy generated JAR from build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]

