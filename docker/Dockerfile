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
  && yarn cache clean

ADD firestore.rules /etc/firebase/
ADD firestore.indexes.json /etc/firebase/
ADD firebase.json /home/node/

EXPOSE 8080
CMD ["firebase", "emulators:start", "--only", "firestore"]
