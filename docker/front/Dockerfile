FROM node:16.13.2-alpine
RUN mkdir -p /var/www/front
WORKDIR /var/www/front

RUN apk update && \
    apk upgrade && \
    yarn global add create-nuxt-app

ENV HOST 0.0.0.0
EXPOSE 3000
ENTRYPOINT ["yarn", "run", "dev"]
