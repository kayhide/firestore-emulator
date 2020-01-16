# Firestore Emulator Docker Image

Image is hosted at
[dockerhub](https://hub.docker.com/repository/docker/kayhide/firestore-emulator).

## How to Use

```console
$ docker run -p 38080:8080 kayhide/firestore-emulator:latest
```

The container exposes port 8080.
In the command above, it is mapped to the host-side of port 38080.

You can access the emulator at `localhost:38080` by setting env var as:

```
FIRESTORE_EMULATOR_HOST=localhost:38080
```

### Configure Security Rules and Indexes

Security rules and indexes are read from the folowing files respectively:

```
/etc/firebase
├── firestore.indexes.json
└── firestore.rules
```

To configure them, mount host files when starting a docker container as:

```console
$ docker run -v $(pwd)/firestore.rules:/etc/firebase/firestore.rules -v $(pwd)/firestore.indexes.json:/etc/firebase/firestore.indexes.json kayhide/firestore-emulator:latest
```


## How to Build

```console
$ bin/build
```

## How to Push

```console
$ bin/push
```
