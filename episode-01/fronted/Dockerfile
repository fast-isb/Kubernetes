# Build Stage
FROM node:14 AS build

# Set working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the entire frontend source code to the container
COPY . .

# Build the production-ready frontend code
RUN npm run build

# Production Stage
FROM nginx:stable-alpine

# Copy built frontend code from the build stage to Nginx server directory
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose port 80 to allow access to the frontend application served by Nginx
EXPOSE 80

# Start Nginx web server in the foreground
CMD ["nginx", "-g", "daemon off;"]
