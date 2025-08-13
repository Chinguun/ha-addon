# ARG BUILD_FROM
# FROM $BUILD_FROM

FROM node:14-slim
ENV CK_API_ENV=prod
# Fix for Debian Buster EOL - Point to the archive repositories
RUN sed -i 's/deb.debian.org/archive.debian.org/g' /etc/apt/sources.list
RUN sed -i 's|security.debian.org/debian-security|archive.debian.org/debian-security|g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y python build-essential
RUN mkdir -p /workspace/node_modules
COPY ["./dist", "./package.json", "/workspace/"]
WORKDIR /workspace
RUN npm install --production --save-exact
COPY ["./node_modules", "/workspace/node_modules/"]
EXPOSE 3000
CMD npm start
