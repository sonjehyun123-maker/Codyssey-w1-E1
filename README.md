# Codyssey-w1-E1
Week 1 / E1

## 제출 저장소 및 기술 문서
### 프로젝트 개요
    스스로 개발환경 구성 및 docker에 대한 이해

### 실행환경 (OS/쉘/터미널, docker, git 버전)
    명령어
    ```terminal
    uname
    echo $SHELL
    echo $TERM
    docker --version
    git --version
    ```
    결과
    ```terminal
    Linux
    /bin/bash
    xterm-256color
    Docker version 28.5.1-1, build e180ab8ab82d22b7895a3e6e110cf6dd5c45f1d7
    git version 2.52.0
    ```

### 수행목록 체크 리스트
#### [v] 터미널 기본 조작 및 폴더 구성
    명령어
    ```terminal
    pwd
    mkdir test test0
    ls
    ls -l
    rm -r test0
    cd test
    pwd
    ```
    
    결과
    ```terminal
    /workspaces/Codyssey-w1-E1
    README.md  test  test0
    total 12
    -rw-rw-rw-  1 codespace root      1124 Apr  3 07:37 README.md
    drwxrwxrwx+ 2 codespace codespace 4096 Apr  3 07:40 test
    drwxrwxrwx+ 2 codespace codespace 4096 Apr  3 07:40 test0
    /workspaces/Codyssey-w1-E1/test
    ```

#### [v] 권한 변경 실습
    명령어
    ```termnial
    touch d1.txt
    ls -l
    chmod u-r d1.txt
    ls -l
    chmod u+r d1.txt
    ls -l
    ```
    결과
    ```termial
    total 0
    -rw-rw-rw- 1 codespace codespace 0 Apr  3 07:41 d1.txt
    total 0
    --w-rw-rw- 1 codespace codespace 0 Apr  3 07:41 d1.txt # userd에서 r이 사라짐 //266
    total 0
    -rw-rw-rw- 1 codespace codespace 0 Apr  3 07:41 d1.txt
    ```
    
#### [x] Docker 설치/점검 // hello-world 실행
    명령어
    ```terminal
    docker --version
    docker info
    docker pull nginx
    docker images
    docker ps -a
    docker run hello-world
    docker logs d2bcf77e00c5
    docker stats
    ```
    결과
    ```terminal
    Docker version 28.5.1-1, build e180ab8ab82d22b7895a3e6e110cf6dd5c45f1d7

    <.,, docker info ,,,>

    Using default tag: latest
    latest: Pulling from library/nginx
    Digest: sha256:7150b3a39203cb5bee612ff4a9d18774f8c7caf6399d6e8985e97e28eb751c18
    Status: Image is up to date for nginx:latest
    docker.io/library/nginx:latest


    REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
    nginx         latest    0cf1d6af5ca7   9 days ago    161MB
    hello-world   latest    e2ac70e7319a   10 days ago   10.1kB

    CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS     NAMES
    13cbf98ee051   nginx         "/docker-entrypoint.…"   7 minutes ago    Exited (0) 7 minutes ago              stupefied_thompson
    22baf22759f1   nginx         "/docker-entrypoint.…"   8 minutes ago    Exited (0) 7 minutes ago              beautiful_keller
    d2bcf77e00c5   hello-world   "/hello"                 23 minutes ago   Exited (0) 23 minutes ago             cranky_perlman
    
    Hello from Docker!
    This message shows that your installation appears to be working correctly.

    To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
    3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
    4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

    For more examples and ideas, visit:
    https://docs.docker.com/get-started/

    Hello from Docker!
    This message shows that your installation appears to be working correctly.

    To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
    3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
    4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

    For more examples and ideas, visit:
    https://docs.docker.com/get-started/

    CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT   MEM %     NET I/O   BLOCK I/O   PIDS
    ```

#### [x] Dockerfile 빌드/실행 // 포트 매핑 접속
    명령어
    ```terminal
    pico Dockerfile
    docker build -t nginx .
    docker images 
    docker run -d -p 8080:80 --name container nginx
    docker ps
    docker logs container
    # http://localhost:8080
    ```
    (/localhost:8080.png)
    결과
    ```termial
    [+] Building 1.6s (8/8) FINISHED                                                                                                                                  docker:default
    => [internal] load build definition from Dockerfile                                                                                                                        0.0s
    => => transferring dockerfile: 131B                                                                                                                                        0.0s
    => [internal] load metadata for docker.io/library/nginx:alpine                                                                                                             1.0s
    => [auth] library/nginx:pull token for registry-1.docker.io                                                                                                                0.0s
    => [internal] load .dockerignore                                                                                                                                           0.0s
    => => transferring context: 2B                                                                                                                                             0.0s
    => [internal] load build context                                                                                                                                           0.0s
    => => transferring context: 9.35kB                                                                                                                                         0.0s
    => CACHED [1/2] FROM docker.io/library/nginx:alpine@sha256:e7257f1ef28ba17cf7c248cb8ccf6f0c6e0228ab9c315c152f9c203cd34cf6d1                                                0.0s
    => [2/2] COPY . /usr/share/nginx/html/                                                                                                                                     0.0s
    => exporting to image                                                                                                                                                      0.4s
    => => exporting layers                                                                                                                                                     0.4s
    => => writing image sha256:89b557f30457bfc5688e73ee6e00166bea2f395aab2129a3d17d56dbf1da846c                                                                                0.0s
    => => naming to docker.io/library/nginx              
                                                                                                                          0.0s
                                                                                                                        
    REPOSITORY    TAG       IMAGE ID       CREATED          SIZE
    nginx         latest    89b557f30457   1 second ago     62.2MB
    hello-world   latest    2d48d0662b14   11 minutes ago   62.2MB
    nginx         <none>    0cf1d6af5ca7   9 days ago       161MB
    hello-world   <none>    e2ac70e7319a   10 days ago      10.1kB

    0e64fc9696fc986ba2c38110d2078a609a4b51f9cdec43e8949bc2c5f0481347
    CONTAINER ID   IMAGE     COMMAND                  CREATED                  STATUS                  PORTS                                     NAMES
    0e64fc9696fc   nginx     "/docker-entrypoint.…"   Less than a second ago   Up Less than a second   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   container
    
    /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
    /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
    /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
    10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
    10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
    /docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
    /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
    /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
    /docker-entrypoint.sh: Configuration complete; ready for start up
    2026/04/03 10:48:47 [notice] 1#1: using the "epoll" event method
    2026/04/03 10:48:47 [notice] 1#1: nginx/1.29.7
    2026/04/03 10:48:47 [notice] 1#1: built by gcc 15.2.0 (Alpine 15.2.0) 
    2026/04/03 10:48:47 [notice] 1#1: OS: Linux 6.8.0-1044-azure
    2026/04/03 10:48:47 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1024:524288
    2026/04/03 10:48:47 [notice] 1#1: start worker processes
    2026/04/03 10:48:47 [notice] 1#1: start worker process 30
    2026/04/03 10:48:47 [notice] 1#1: start worker process 31
    2026/04/03 10:48:47 [notice] 1#1: start worker process 32
    2026/04/03 10:48:47 [notice] 1#1: start worker process 33
    ```


#### [x] 바인드 마운트 반영
    명령어
    ```termial
    docker run -it -v $(pwd)/test:/app --name new-container ubuntu bash
    #------------container---------------
    mkdir test
    cd test
    vim day.txt
    #--------------day-----------------
    hello world

    123
    #---------------------------------
    cat day.txt

    ```
    결과
    ```termial
    ```

#### [x] 볼륨 영속성
    명령어
    ```termial
    ```
    결과
    ```termial
    ```

#### [x] Git 설정 + VSCode GitHub 연동
    명령어
    ```termial
    ```
    결과
    ```termial
    ```

### 트러블슈킹(2회이상)
