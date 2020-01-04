# Build from node image
FROM node:latest

# We will be running from /app directory
WORKDIR /app

# Copy built app from dist direcotry to container
COPY dist ./dist

# Give access to port 5000
EXPOSE 5000/tcp

# Install serve and serve the app
RUN npm install -g serve

CMD serve -s -l 5000 dist

