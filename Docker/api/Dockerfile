FROM node:12

WORKDIR /app

COPY package*.json ./

RUN npm i -g @adonisjs/cli \
    && npm i --save pg sqlite3 mysql @adonisjs/ignitor \
    && npm install

COPY . .

EXPOSE 3333

CMD [ "adonis", "serve", "--dev" ]
