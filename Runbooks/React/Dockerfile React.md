Dockerfile React
```dockerfile
# Build Container

FROM node:14 as build
COPY . .
RUN npm install
RUN npm run build

# Production Container

FROM nginx:stable-alpine
COPY --from=build /build/ /usr/share/nginx/html
COPY --from=build /nginx/nginx.conf /etc/nginx/conf.d/default.conf
```	