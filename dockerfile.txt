# Use the official Node.js LTS image as the base image
FROM node:alpine

# Set the working directory inside the container
WORKDIR /usr/src/app
# Copy package.json and yarn.lock files to the container
COPY package.json yarn.lock ./

# Install application dependencies in a separate layer
RUN yarn install --frozen-lockfile

# Copy the rest of the application code to the container
COPY . .

# Expose port 3000
EXPOSE 3000

# Command to start the application
CMD ["yarn", "start"]