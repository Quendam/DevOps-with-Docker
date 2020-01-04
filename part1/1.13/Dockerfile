# Build from node image
FROM openjdk:8u232-slim-buster

# Set working direcotry
WORKDIR /app

# Install git
RUN apt-get update && apt-get install -y git

# Clone backend code
RUN git clone https://github.com/docker-hy/spring-example-project.git .

# Build
RUN ./mvnw package

# Expose port
EXPOSE 8080

# And finaly run
CMD java -jar ./target/docker-example-1.1.3.jar
