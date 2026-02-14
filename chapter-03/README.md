# Source Code Chapter 3
You will find example solutions discussed in **Chapter 03, Mastering Containers** of the book in the `solutions` subfolder.

    docker container run alpine echo "Hello World"
    docker container run quay.io/centos/centos echo "Hello from centos"
    docker container run --detach --name trivia fundamentalsofdocker/trivia:ed4
    docker container run --detach quay.io/centos/centos:stream9 sleep 3600
    docker container run -d --name nginx -p 8080:80 nginx:alpine
    docker container run --name test -it --log-driver none busybox sh -c 'for N in 1 2 3; do echo "Hello $N"; done'

    docker container ls -l
    docker container ls --all
    docker container ls --quiet
    docker container ls --help

    docker container stop trivia
    export CONTAINER_ID=$(docker container ls -a | grep trivia | awk '{print $1}'); echo $CONTAINER_ID
    docker container stop $CONTAINER_ID
    docker container start $CONTAINER_ID
    docker container start trivia

    docker container rm $CONTAINER_ID
    docker container rm $CONTAINER_ID --force
    docker container rm -f trivia
    docker container rm --force $(docker container ls --all --quiet)
    docker container rm nginx
    docker container rm test

    docker container inspect trivia
    docker container inspect -f "{{json .State}}" trivia | jq .

    docker container exec -i -t trivia /bin/sh
    docker container exec trivia ps
    docker container exec -it -e MY_VAR="Hello World" trivia /bin/sh

    curl -4 localhost:8080

    docker container attach nginx
    for n in {1..10}; do curl -4 localhost:8080; done

    docker container logs trivia
    docker container logs --tail 5 trivia
    docker container logs --tail 5 --follow trivia
    docker container logs test