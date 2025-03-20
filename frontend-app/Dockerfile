# Uses node version 20 as our base image
FROM node:20 AS build

# Goes to the app directory
WORKDIR /app

# Copies the package.json and package-lock.json (if available) 
COPY package.json package-lock.json ./

# Install app dependencies
RUN npm install

# Copies the rest of the application
COPY . .

# Builds the application (this assumes a frontend project with a build step)
RUN npm run build

# Uses a lightweight Nginx image for serving the built application
FROM nginx:alpine

# Copies the built application (from the previous "build" stage) into the Nginx web directory
COPY --from=build /app/dist /usr/share/nginx/html

# Exposes port 80 so the container can serve the application
EXPOSE 80

# Starts the Nginx server in the foreground 
CMD ["nginx", "-g", "daemon off;"]
