# client/Dockerfile

# This is the build file for the client module,
# Docker will use this to setup the client container image.

# Installs the node image
FROM node

# Creates the client directory in the container
RUN mkdir -p /app/client
# Sets the working directory to the client directory
WORKDIR /app/client

# Copies the yarn.lock file to the container
COPY yarn.lock /app/client/
# Copies the package.json to the container
COPY package*.json /app/client/

# Installs the client dependencies
RUN yarn install

# Copies the files from the client directory to the container
COPY . /app/client/

# Runs the client
CMD ["yarn", "start"] 

###############################################################################

# # build environment
# FROM node:12.2.0-alpine as build
# WORKDIR /app/client
# ENV PATH /app/client/node_modules/.bin:$PATH
# COPY package.json /app/client/
# RUN yarn install
# RUN yarn add react-scripts@3.0.1 -g --silent
# COPY . /app/client/
# RUN yarn run build

# # production environment
# FROM nginx:1.16.0-alpine
# COPY --from=build /app/client/build /usr/share/nginx/html
# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]