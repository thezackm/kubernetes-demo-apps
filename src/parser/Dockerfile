FROM node:18-alpine

ENV NEW_RELIC_NO_CONFIG_FILE=true \
    NEW_RELIC_DISTRIBUTED_TRACING_ENABLED=true \
    NEW_RELIC_LOG=stdout \
    NEW_RELIC_RECORD_SQL=obfuscated \
    NEW_RELIC_SLOW_SQL_ENABLED=true \
    NEW_RELIC_APPLICATION_LOGGING_ENABLED=true \
    NEW_RELIC_APPLICATION_LOGGING_METRICS_ENABLED=true \
    NEW_RELIC_APPLICATION_LOGGING_FORWARDING_ENABLED=true \
    NEW_RELIC_CODE_LEVEL_METRICS_ENABLED=true \
    NEW_RELIC_IGNORING_RULES='^.*healthz'

RUN apk --no-cache add --virtual native-deps \
g++ gcc libgcc libstdc++ linux-headers autoconf automake make nasm python3 git && \
npm install --quiet node-gyp -g

RUN mkdir -p /usr/src/app/
WORKDIR /usr/src/app/

COPY package.json .
RUN npm install

COPY index.js .

EXPOSE 3000

CMD [ "node", "index.js" ]
