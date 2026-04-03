# Codyssey-w1-E1
Week 1 / E1

## 제출 저장소 및 기술 문서
### 프로젝트 개요
    스스로 개발환경 구성 및 docker에 대한 이해

### 실행환경 (OS/쉘/터미널, docker, git 버전)


### 수행목록 체크 리스트
#### [v] 터미널 기본 조작 및 폴더 구성
    명령어
    ```bash
    pwd
    mkdir test test0
    ls
    ls -l
    rm -r test0
    cd test
    pwd
    ```
    
    결과
    ```
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
    ```termial
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
    --w-rw-rw- 1 codespace codespace 0 Apr  3 07:41 d1.txt
    total 0
    -rw-rw-rw- 1 codespace codespace 0 Apr  3 07:41 d1.txt
    ```
    
- [x] Docker 설치/점검
    명령어
    ```
- [x] hello-world 실행
- [x] Dockerfile 빌드/실행
- [x] 포트 매핑 접속(2회)
- [x] 바인드 마운트 반영
- [x] 볼륨 영속성
- [x] Git 설정 + VSCode GitHub 연동

### 트러블슈킹(2회이상)
