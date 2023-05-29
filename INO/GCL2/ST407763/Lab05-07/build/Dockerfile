FROM node:latest
RUN apt update
RUN apt-get install -y git && apt install -y npm
RUN git clone https://github.com/squirrellyjs/squirrelly.git
WORKDIR squirrelly
RUN npm install && npm install -g npm@9.6.2 && npm run build
