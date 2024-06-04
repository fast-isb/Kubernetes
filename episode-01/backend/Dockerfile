# Use node:14 as base image
FROM node:14

# Set working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application source code to container
COPY . .

# Expose port 5000
EXPOSE 5000

# Command to run the backend server
CMD ["node", "src/server.js"]
