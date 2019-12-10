FROM node:8-alpine

#RUN mkdir -p /usr/src/app
#
#WORKDIR /usr/src/app

# Create app directory
WORKDIR /var/www

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
#COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm install --only=production

# Bundle app source
COPY . .

RUN apk update && apk upgrade \
	&& apk add --no-cache git \
	&& apk --no-cache add --virtual builds-deps build-base python \
	&& npm install -g nodemon npm-run-all node-gyp node-pre-gyp && npm install\
	&& npm rebuild bcrypt --build-from-source

#RUN apk update && apk add bash
#RUN apk add --no-cache bash
RUN npm install
#RUN npm run build

EXPOSE 5000

CMD [ "npm", "start" ]
