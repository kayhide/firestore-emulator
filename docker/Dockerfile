FROM node:lts-alpine
ENV HOME=/home/node
WORKDIR $HOME

RUN apk update \
  && apk --no-cache add openjdk11-jre-headless \
  && rm -rf /var/cache/apk/* \
  && yarn global add firebase-tools \
  && firebase setup:emulators:firestore \
  && find .cache -name "cloud-firestore-emulator-v*.jar" \
  | sed -e 's/^.*-v\([0-9.]*\)\.jar$/\1/' \
  > .version \
  && chown -R node:node $HOME \
  && yarn cache clean

ADD firebase.json /home/node/
ADD firestore.rules /home/node/
ADD firestore.indexes.json /home/node/

USER node
EXPOSE 8080
CMD ["firebase", "emulators:start", "--only", "firestore"]