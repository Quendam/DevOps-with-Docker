# Build from node image
FROM node:latest

# We will be running from /app directory
WORKDIR /app

# Copy app src from local direcotry to container
COPY frontend-example-docker ./

# Install node modules
RUN npm install

# Give access to port 5000
EXPOSE 5000/tcp

CMD API_URL=http://192.168.1.50:8000/ npm start

