# Use an official Maven image as the base image
FROM maven:3.8.4-openjdk-11-slim AS build

# Set the working directory in the container
WORKDIR /app

# Copy the pom.xml and the project files to the container
COPY pom.xml .
COPY src ./src

# Build the application using Maven
RUN mvn clean package -DskipTests
RUN mv /app/target/*.jar /app/target/my-maven-docker-project.jar
# Specify the location for the JAR file within the build stage
# Move the JAR file to /app/target directory



# Use an official OpenJDK image as the base image
FROM openjdk:11-jre-slim

# Set the working directory in the container
WORKDIR /app

# Copy the built JAR file from the previous stage to the container
COPY --from=build /app/target/my-maven-docker-project.jar .

# Set the command to run the application
CMD ["java", "-jar", "my-maven-docker-project.jar"]
