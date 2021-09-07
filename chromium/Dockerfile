FROM alpine:latest

# Installs latest Chromium package.
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" > /etc/apk/repositories \
    && echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
    && echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
    && echo "http://dl-cdn.alpinelinux.org/alpine/v3.12/main" >> /etc/apk/repositories \
    && apk upgrade -U -a \
    && apk add  libstdc++ chromium harfbuzz nss freetype ttf-freefont font-noto-emoji wqy-zenhei \
    && rm -rf /var/cache/* && mkdir /var/cache/apk

RUN mkdir -p /usr/src/app \
    && adduser -D chrome \
    && chown -R chrome:chrome /usr/src/app
USER chrome
WORKDIR /usr/src/app

ENV CHROME_BIN=/usr/bin/chromium-browser \
    CHROME_PATH=/usr/lib/chromium/

ENTRYPOINT ["chromium-browser", "--headless", "--use-gl=swiftshader", "--disable-software-rasterizer", "--disable-dev-shm-usage"]