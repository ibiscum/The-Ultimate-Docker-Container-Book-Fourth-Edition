# Source Code Chapter 4
You will find example solutions discussed in **Chapter 04, Creating and Managing Containers** of the book in the `solutions` subfolder.

    docker container run -it --name sample alpine:3.21 /bin/sh
    apk update && apk add curl
    curl -I https://google.com
    docker container ls -a | grep sample
    docker container diff sample
    docker container commit sample my-alpine
    docker image ls
    docker image history my-alpine

    docker image build -t pinger .
    docker container run --rm -it pinger
    docker container run --rm -it pinger -w 5 127.0.0.1
    docker container run --rm -it --entrypoint ash pinger

    docker image build -t my-ubuntu .
    docker image build -t my-ubuntu -f Dockerfile .

    docker image build -t hello-world .
    docker image ls | grep hello-world
    docker image build -t hello-world-small -f Dockerfile.multi-step .
