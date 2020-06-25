FROM node:lts-alpine

# set app serving to permissive / assigned
ENV NUXT_HOST=0.0.0.0
# set app port
ENV NUXT_PORT=3000

# update and install dependency
RUN apk --no-cache add python make g++ curl
RUN npm i -g pm2 npm-run-all && npm cache clean --force

# create destination directory
RUN mkdir -p /app
WORKDIR /app

EXPOSE 3000
EXPOSE 9229

HEALTHCHECK CMD curl --fail http://localhost:3000/healthcheck/ || exit 1

# start the app
CMD [ "pm2-runtime", "npm", "--name", "nuxt", "--", "start" ]
