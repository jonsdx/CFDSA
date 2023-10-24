FROM node:18

LABEL name=test-container

WORKDIR /app

COPY ./ .

RUN npm ci

ENV INSTANCE_NAME=Bear
ENV INSTANCE_HASH=Bear_test
ENV PORT=5000 APP_DIR=/app

VOLUME ${APP_DIR}/public

EXPOSE ${PORT}

HEALTHCHECK --interval=1m --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s http://localhost:${PORT}/healthz || exit 1

ENTRYPOINT node main.js 