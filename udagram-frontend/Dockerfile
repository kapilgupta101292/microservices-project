## Build Stage
FROM beevelop/ionic AS ionic

# Create and change the Working directory
WORKDIR /usr/src/app

# Copy package json and Install app dependencies
COPY *.json ./
RUN npm ci

# copy app source
COPY . .

# RUN ionic build
RUN ionic build

## Run
FROM nginx:alpine

#Use previous stage and copy the source files to serve via nginx
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html