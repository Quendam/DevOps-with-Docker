# Build from node image
FROM node:latest

# Set working direcotry
WORKDIR /app

# Install git
RUN apt-get install -y git

# Clone backend code
RUN git clone https://github.com/Quendam/glowing-spork.git .

# Install required node packages
RUN npm i

# Expose port
EXPOSE 3000
EXPOSE 3001

# And finaly run the backend
CMD npm run both
