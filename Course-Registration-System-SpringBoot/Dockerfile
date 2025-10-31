# Use Eclipse Temurin JDK for Java 21
FROM eclipse-temurin:21-jdk

# Set work directory inside container
WORKDIR /app

# Copy Maven files first (for caching)
COPY pom.xml .
COPY mvnw .
COPY .mvn .mvn

# Install dependencies
RUN ./mvnw dependency:go-offline

# Copy project source code
COPY src src

# Build project
RUN ./mvnw clean package -DskipTests

# Expose backend port
EXPOSE 8080

# Run jar
ENTRYPOINT ["java", "-jar", "target/Course-Registration-System-0.0.1-SNAPSHOT.jar"]
