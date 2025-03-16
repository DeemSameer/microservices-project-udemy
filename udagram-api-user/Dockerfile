# FROM node:18
# ## Create app directory
# WORKDIR /usr/src/app
# ## Install app dependencies
# ## A wildcard is used to ensure both package.json AND package-lock.json are copied where available (npm@5+)
# COPY package*.json ./
# RUN npm ci 
# ## Bundle app source
# COPY . .
# EXPOSE 8080
# CMD [ "npm", "run", "prod" ]

# Use NodeJS base image
FROM node:13

# Create app directory in Docker
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies in Docker
RUN npm install

# Copy app from local environment into the Docker image
COPY . .

# Set the API’s port number
EXPOSE 8080

# Define Docker’s behavior when the image is run
CMD ["npm", "run", "prod"]