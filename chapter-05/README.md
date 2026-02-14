# Source Code Chapter 5
You will find example solutions discussed in **Chapter 05, Data Volumes and Configuration** of the book in the `solutions` subfolder.

    docker container run --name demo alpine /bin/sh -c 'echo "This is a test" > sample.txt'
    docker container diff demo
    docker volume create sample
    docker volume inspect sample

    docker container run --name test -it -v sample:/data alpine /bin/sh
    cd /data
    echo "Some data" > data.txt
    echo "Some more data" > data2.txt
    docker container rm test
    docker container run --name test2 -it --rm -v sample:/app/data centos:7 /bin/bash
    docker volume rm sample
    docker volume ls
    docker container rm -v -f $(docker container ls -aq)
    docker container run -it --privileged --pid=host debian nsenter -t 1 -m -u -n -i sh