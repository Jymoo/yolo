# Base image
FROM node:14-alpine

# Set working directory
WORKDIR /home/vagrant/YoloApp/

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install --silent

# Copy the remaining backend files
COPY . .

EXPOSE 3000
# Start the app
CMD ["npm", "start"]
