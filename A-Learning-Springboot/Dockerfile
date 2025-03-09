# Use a lightweight JDK 21 image
FROM eclipse-temurin:21-jdk AS build

# Set working directory inside the container
WORKDIR /app

# Copy only the necessary files to build the application
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN chmod +x mvnw && ./mvnw dependency:go-offline

# Copy the entire source code and build the JAR
COPY src ./src
RUN ./mvnw clean package -DskipTests

# Use a smaller JDK image for running the application
FROM eclipse-temurin:21-jre AS runtime

# Set working directory
WORKDIR /app

# Copy the built JAR from the previous stage
COPY --from=build /app/target/A-Learning-Springboot-0.0.1-SNAPSHOT.jar app.jar

# Expose the application port
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "app.jar"]
