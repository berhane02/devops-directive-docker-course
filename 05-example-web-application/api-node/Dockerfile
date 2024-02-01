FROM node:current-alpine3.19

WORKDIR /usr/src/app

ENV NODE_ENV production

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/app/.npm \
  npm set cache /usr/src/app/.npm && \
  npm ci --only=production

USER node

COPY --chown=node:node ./src .

COPY . .

EXPOSE 3000

CMD [ "npm", "run", "dev" ]