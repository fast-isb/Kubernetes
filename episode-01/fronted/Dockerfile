# Use a Node.js image as base
FROM node:latest as build

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

RUN npm cache clean --force

# Install dependencies
RUN npm install

# Copy the rest of your application
COPY . .

# Build the frontend
RUN npm run build

# Use nginx to serve the production build
FROM nginx:alpine

# Copy the build output from the previous stage to nginx's html directory
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose port 80 to serve the frontend
EXPOSE 80

# Nginx is already started by default in the nginx:alpine image
# No need to define the CMD, it will serve the static files automatically
