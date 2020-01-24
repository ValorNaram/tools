FROM node:lts-alpine
LABEL maintainer="Malte Dölker" organization="Trufi Association e.V."

RUN mkdir /data
VOLUME /data

ENV TARGET="bolivia-cochabamba"
ENV FILENAME="gtfs.zip"

CMD npm install -g gtfs-${TARGET} \
    && gtfs-${TARGET} /data/${FILENAME}
