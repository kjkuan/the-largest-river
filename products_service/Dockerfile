
# FROM node:16.15.1-alpine
# COPY . /app
# WORKDIR /app
# COPY package.json/ ./
# COPY package-lock.json ./
# # COPY /Users/bhoyer/certs/dynamic-shark/root.crt ./
# # COPY /../../foo.txt /app/foo.txt
# COPY ./ ./
# RUN npm install
# CMD npm start

FROM node:16.15.1-alpine
COPY . /app
WORKDIR /app

COPY package.json /app/package.json
COPY package-lock.json /app/package-lock.json

# only needed when connecting to YB Managed nodes
# COPY /certs /app/certs

RUN npm install
RUN apk update && apk add bash
RUN apk add postgresql-client

# Add entrypoint script
COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint
RUN chmod +x /usr/local/bin/docker-entrypoint

ENTRYPOINT ["sh", "./docker-entrypoint.sh"]
CMD []