#
# ---- Base Node ----
FROM node:alpine AS base
# Set working directory
WORKDIR /root/app
# Copy project file
COPY package.json .

#
# ---- Dependencies ----
FROM base as dependencies

# Install node packages
RUN npm set progress=false && npm config set depth 0
RUN npm install --only=production
# Copy production node_modules aside
RUN cp -R node_modules prod_node_modules
# Install ALL node_modules, including 'devDependencies'
RUN npm install

#
# ---- Test(Chrome) ----
FROM dependencies as test
RUN echo @edge http://nl.alpinelinux.org/alpine/edge/community >> /etc/apk/repositories \
  && apk add --no-cache \
  # Chromium dependencies
  nss@edge \
  chromium-chromedriver@edge \
  chromium@edge

USER node

ENV CHROME_BIN /usr/bin/chromium-browser
COPY . .

#
# ---- Release ----
FROM base AS release
# Copy production node_modules
COPY --from=dependencies /root/app/prod_node_modules ./node_modules
# Copy app sources
COPY . .
# Expose port and define CMD
EXPOSE 4200
CMD npm run start