Dockerfile Nodejs

```dockerfile
FROM node:14

# Init system designed for docker for better signal handling

RUN apt update && apt install dumb-init

# Create node user to avoid running app as root (SecOps)

USER node
COPY --chown=node:node . ./app
WORKDIR /app

# Install dependecies without bringing in devDependencies

RUN npm ci --only=production

# Enable production mode for all dependecies

ENV NODE_ENV production

RUN npm run seed

# TODO DON'T pass secrets this way.

# (also change this secret, since its no longer secret)

ENV JWT_SECRET sTrInGoNaLuNgAeCaTtIvIsSiMa1234567890
ENV JWT_EXPIRES_IN 1d

EXPOSE 4000
CMD [ "dumb-init", "node", "/bin/www" ]
```