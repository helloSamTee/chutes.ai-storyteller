FROM n8nio/n8n:1.121.0
USER root

RUN apk add --no-cache python3 py3-pip ffmpeg

RUN mkdir -p /files && chown -R node:node /files

USER node
