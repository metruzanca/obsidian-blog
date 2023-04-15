# React App Dockerfile
Designed to be used with CI pipelines. Able to call `docker run --target test` for only test and `docker run` for actual build.

```dockerfile
# Install node packages
FROM node:12 as build
WORKDIR /app
COPY package*.json .
RUN npm ci
COPY . .

# Run all test suits
RUN npm test

# Create build
RUN npm run build

# Copy only necessary files from build stage
FROM nginx as deploy
COPY --from=build /app/build/ /usr/share/nginx/html
COPY --from=build /nginx.conf /etc/nginx/conf.d/default.conf
```