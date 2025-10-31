# Use Maven with JDK 21 to build the application
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app

# Copy the entire project
COPY . .

# Build the JAR file
RUN mvn clean package -DskipTests

# Use lightweight JDK to run the app
FROM eclipse-temurin:21-jdk
WORKDIR /app

# Copy built JAR from builder stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
