FROM --platform=$TARGETPLATFORM node:22-alpine

RUN apk add --no-cache \
    gcc \
    python3 \
    pypy3 \
    g++ \
    fpc \
    fp-compiler \
    openjdk17-jdk-headless \
    rust \
    ghc \
    cabal \
    gjs \
    go \
    ruby \
    mono-runtime \
    mono-mcs \
    kotlin \
    php83 \
    php83-cli \
    nodejs \
    bash

RUN apk add --no-cache python2

ADD ./entrypoint.sh /root/entrypoint.sh
ADD ./judge.yaml /root/judge.yaml
ADD ./judge.yaml /root/.hydro/judge.yaml
RUN chmod +x /root/entrypoint.sh

RUN yarn global add pm2 @hydrooj/hydrojudge && \
    wget https://github.com/criyle/go-judge/releases/download/v1.8.0/go-judge_1.8.0_linux_amd64 -O /usr/bin/sandbox && \
    chmod +x /usr/bin/sandbox

ENTRYPOINT /root/entrypoint.sh
