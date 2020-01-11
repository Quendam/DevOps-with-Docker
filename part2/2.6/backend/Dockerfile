# Build from node image
FROM node:latest

# Set working direcotry
WORKDIR /app

# Install git
RUN apt-get install -y git

# Clone backend code
RUN git clone https://github.com/docker-hy/backend-example-docker.git .

# Install required node packages
RUN npm i

# Expose port
EXPOSE 8000

# Define frontend url
ENV FRONT_URL=http://192.168.1.50:5000

# And finaly run the backend
CMD npm start
