FROM debian:bookworm-20251117

ARG SOURCE_REPO=https://github.com/herenow/wsProxy.git
ARG COMMIT_SHA=d5fba981ec1a9ef08cbf6a206c020537b8a96e00

LABEL org.opencontainers.image.source="https://github.com/mestre8d/wsproxy-docker"
LABEL org.opencontainers.image.description="Contains a herenow/wsProxy compilation environment in Debian."

RUN apt-get update && apt-get install -y ca-certificates curl git nodejs npm && \
    rm -rf /var/lib/apt/lists/* && mkdir -p /app && npm install -g ws

WORKDIR /app

RUN git clone $SOURCE_REPO . && git checkout $COMMIT_SHA && rm -rf .git \
    && npm install && npm link

RUN chown 1000:1000 -R /app

USER 1000

EXPOSE 5999

CMD ["wsproxy"]