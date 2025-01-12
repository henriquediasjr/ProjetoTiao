# Stage 1: Build the React app using Node.js 20
FROM node:20 AS build

WORKDIR /app

# Copy package.json and package-lock.json for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build

# Stage 2: Serve the built application using a lightweight image
FROM nginx:alpine

# Copy the built files to the nginx HTML folder
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80 to access the app
EXPOSE 80

# Start the nginx server
CMD ["nginx", "-g", "daemon off;"]
