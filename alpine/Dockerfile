FROM alpine:20250108

ARG SOURCE_REPO=https://github.com/herenow/wsProxy.git
ARG COMMIT_SHA=d5fba981ec1a9ef08cbf6a206c020537b8a96e00

RUN apk update && apk upgrade && apk add --no-cache nodejs npm git ca-certificates && mkdir -p /app && npm install -g ws

WORKDIR /app

RUN git clone $SOURCE_REPO . && git checkout $COMMIT_SHA && rm -rf .git \
    && npm install && npm link

RUN chown 1000:1000 -R /app

USER 1000

EXPOSE 5999

CMD ["wsproxy"]
