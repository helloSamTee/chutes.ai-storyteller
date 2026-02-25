FROM n8nio/n8n:latest

USER root

# Reinstall apk-tools since n8n removes it
RUN ARCH=$(uname -m) && \
    wget -qO- "http://dl-cdn.alpinelinux.org/alpine/latest-stable/main/${ARCH}/" | \
    grep -o 'href="apk-tools-static-[^"]*\.apk"' | head -1 | cut -d'"' -f2 | \
    xargs -I {} wget -q "http://dl-cdn.alpinelinux.org/alpine/latest-stable/main/${ARCH}/{}" && \
    tar -xzf apk-tools-static-*.apk && \
    ./sbin/apk.static -X http://dl-cdn.alpinelinux.org/alpine/latest-stable/main \
        -U --allow-untrusted add apk-tools && \
    rm -rf sbin apk-tools-static-*.apk

RUN apk add --no-cache python3 py3-pip py3-virtualenv ffmpeg

RUN mkdir -p /home/node/.n8n/python && \
    mkdir -p /home/node/.n8n/output && \
    python3 -m venv /home/node/.n8n/python/venv && \
    chown -R node:node /home/node/.n8n

    
USER node