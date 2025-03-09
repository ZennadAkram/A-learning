# Use a lightweight JDK 21 image
FROM eclipse-temurin:21-jdk

# Set the working directory
WORKDIR /app

# Copy the project files
COPY . .

# Build the application
RUN chmod +x mvnw && ./mvnw clean package -DskipTests

# Run the application
CMD ["java", "-jar", "target/*.jar"]
