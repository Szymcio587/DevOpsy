FROM node:latest

RUN apt update
RUN apt install -y git && apt install -y npm
RUN git clone https://github.com/squirrellyjs/squirrelly.git
WORKDIR /squirrelly
RUN npm i -g npm && npm build
