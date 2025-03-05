### Build
FROM beevelop/ionic:latest AS ionic
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm install --force 
## Bundle app source
COPY . .
RUN  export NODE_OPTIONS=--openssl-legacy-provider && ionic build
### Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf 
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html








# FROM node:18-alpine

# # Set the working directory in the container
# WORKDIR /app

# # Copy package.json and package-lock.json (or yarn.lock)
# COPY package*.json ./

# # Install dependencies
# RUN npm install --force

# # Copy the Ionic project files
# COPY . .

# # Install Ionic CLI globally (if not already present in the image)
# RUN npm install -g @ionic/cli@7.2.0

# # Build the Ionic app
# RUN export NODE_OPTIONS=--openssl-legacy-provider && ionic build 

# # Expose the port your application will run on (if needed)
# # Example for a static server:
# # EXPOSE 8100

# # Command to run the app (adjust as needed)
# # Example for a static server:
# # CMD ["npx", "serve", "www", "-l", "8100"]

# #Example for capacitor/cordova
# #CMD ["npx", "cap", "run", "android", "-l", "--external"]

# #Example for just serving the build folder with nginx
# FROM nginx:alpine

# COPY nginx.conf /etc/nginx/conf.d/default.conf 
# COPY --from=0 /app/www /usr/share/nginx/html

# EXPOSE 80

# CMD ["nginx", "-g", "daemon off;"]