# Build from node image
FROM node:latest

# We will be running from /app directory
WORKDIR /app

# Install git
RUN apt-get install -y git

# Clone backend code
RUN git clone https://github.com/docker-hy/frontend-example-docker .

# Install node modules
RUN npm install

# Give access to port 5000
EXPOSE 5000/tcp

CMD npm start

