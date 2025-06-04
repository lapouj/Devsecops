FROM node:12-alpine3.9

WORKDIR /myapp

COPY package.json /myapp/

RUN npm install --production
# L'option production permet de n’installer que les dépendances nécessaires à l’exécution de l’application (et pas celles destinées au développement)
# ça permet notament de limiter la surface d'attaque en prod

COPY src/ /myapp/src/

CMD ["node", "src/index.js"]