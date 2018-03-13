FROM node:alpine
WORKDIR /root/app
COPY package.json .

# Install node packages
RUN npm set progress=false && npm config set depth 0
RUN npm install --only=production
