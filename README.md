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

## How to Build

```console
$ bin/build
```

## How to Push

```console
$ bin/push
```
