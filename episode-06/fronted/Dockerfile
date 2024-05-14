# Use the official Node.js image as the base image
FROM node:14

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build

# Install a simple HTTP server to serve static files
RUN npm install -g serve

# Expose the port the application runs on
EXPOSE 5000

# Start the application
CMD ["serve", "-s", "build"]