FROM node:12-alpine3.9

WORKDIR /myapp

COPY package.json /myapp/

RUN npm install --production
# On réduit les dépendances

COPY src/ /myapp/src/

CMD ["node", "src/index.js"]