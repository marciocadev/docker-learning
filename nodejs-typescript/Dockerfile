### Debug
FROM node:17-alpine3.12 as debug

WORKDIR /work

COPY ./src/package.json /work/package.json
RUN npm install
RUN npm install -g nodemon 

COPY ./src/ /work/src/

ENTRYPOINT ["nodemon", "--inspect=0.0.0.0", "./src/server.ts"]
### Debug


### Pre-prod
FROM node:17-alpine3.12 as preprod

WORKDIR /work

COPY ./src/package.json /work/package.json
RUN npm install
COPY ./src/ /work/
RUN npm run build
### Pre-prod

### Prod
FROM node:17-alpine3.12 as prod

WORKDIR /work

COPY ./src/package.json /work/package.json
RUN npm install --production
COPY --from=preprod /work/server.js .

CMD node .
### Prod