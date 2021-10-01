FROM keymetrics/pm2:12-alpine

WORKDIR /app

ARG NODE_ENV production
ENV NODE_ENV $NODE_ENV
ENV PROSE_DISCOURSE_HOST=https://forum.sienci.com
ENV PROSE_APP_PORT=8888
ENV PROSE_APP_HOSTNAME=0.0.0.0

COPY package.json ./
COPY yarn.lock ./

RUN yarn

COPY tsconfig.json ./
COPY ./src ./src

RUN yarn build

COPY pm2.json .

CMD ["pm2-runtime", "start", "pm2.json"]
