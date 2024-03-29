# use this empty Dockerfile to build your assignment

# This dir contains a Node.js app, you need to get it running in a container
# No modifications to the app should be necessary, only edit this Dockerfile

# Overview of this assignment
# use the instructions from developer below to create a working Dockerfile
# feel free to add command inline below or use a new file, up to you (but must be named Dockerfile)
# once Dockerfile builds correctly, start container locally to make sure it works on http://localhost
# then ensure image is named properly for your Docker Hub account with a new repo name
# push to Docker Hub, then go to https://hub.docker.com and verify
# then remove local image from cache
# then start a new container from your Hub image, and watch how it auto downloads and runs
# test again that it works at http://localhost


# Instructions:
# - you should use the 'node' official image, with the alpine 6.x branch
# - this app listens on port 3000, but the container should launch on port 80
  #  so it will respond to http://localhost:80 on your computer
# - then it should use alpine package manager to install tini: 'apk add --update tini'
# - then it should create directory /usr/src/app for app files with 'mkdir -p /usr/src/app'
# - Node uses a "package manager", so it needs to copy in package.json file
# - then it needs to run 'npm install' to install dependencies from that file
# - to keep it clean and small, run 'npm cache clean --force' after above
# - then it needs to copy in all files from current directory
# - then it needs to start container with command '/sbin/tini -- node ./bin/www'
# - in the end you should be using FROM, RUN, WORKDIR, COPY, EXPOSE, and CMD commands
FROM node:6-alpine

EXPOSE 3000

RUN apk add --update tini \
    && mkdir -p /usr/src/app 

WORKDIR /usr/src/app

COPY package.json package.json

RUN npm install && npm cache clean 

COPY . .

CMD ["tini", "--", "node", "./bin/www"]
