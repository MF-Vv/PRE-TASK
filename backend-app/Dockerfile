# Uses node version 20 as our base image
FROM node:20-alpine

# Goes to the app directory
WORKDIR /app

# Copies the package.json and package-lock.json (if available) 
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copies the rest of the application
COPY . .

# Expose the port so our computer access it
EXPOSE 5000

# Run the app
CMD ["npm", "start"]
