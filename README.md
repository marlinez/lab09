marialuneva@1511:~$ export GITHUB_USERNAME=marlinez
marialuneva@1511:~$ cd ${GITHUB_USERNAME}/workspace
marialuneva@1511:~/marlinez/workspace$ pushd .
~/marlinez/workspace ~/marlinez/workspace
marialuneva@1511:~/marlinez/workspace$ source scripts/activate
marialuneva@1511:~/marlinez/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab07 lab08
fatal: целевой путь «lab08» уже существует и не является пустым каталогом.
marialuneva@1511:~/marlinez/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab07 lab08
Клонирование в «lab08»...
remote: Enumerating objects: 230, done.
remote: Counting objects: 100% (230/230), done.
remote: Compressing objects: 100% (118/118), done.
remote: Total 230 (delta 87), reused 221 (delta 84), pack-reused 0 (from 0)
Получение объектов: 100% (230/230), 1.03 МиБ | 958.00 КиБ/с, готово.
Определение изменений: 100% (87/87), готово.
marialuneva@1511:~/marlinez/workspace$ cd lab08
marialuneva@1511:~/marlinez/workspace/lab08$ git submodule update --init
Подмодуль «third-party/gtest» (https://github.com/google/googletest) зарегистрирован по пути «third-party/gtest»
Клонирование в «/home/marialuneva/marlinez/workspace/lab08/third-party/gtest»...
Submodule path 'third-party/gtest': checked out '2fe3bd994b3189899d93f1d5a881e725e046fdc2'
marialuneva@1511:~/marlinez/workspace/lab08$ git remote remove origin
marialuneva@1511:~/marlinez/workspace/lab08$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab08
marialuneva@1511:~/marlinez/workspace/lab08$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (4/4), 4.73 КиБ | 4.73 МиБ/с, готово.
Из https://github.com/marlinez/lab08
 * branch            master     -> FETCH_HEAD
 * [новая ветка]     master     -> origin/master
подсказка: You have divergent branches and need to specify how to reconcile them.
подсказка: You can do so by running one of the following commands sometime before
подсказка: your next pull:
подсказка: 
подсказка:   git config pull.rebase false  # merge
подсказка:   git config pull.rebase true   # rebase
подсказка:   git config pull.ff only       # fast-forward only
подсказка: 
подсказка: You can replace "git config" with "git config --global" to set a default
подсказка: preference for all repositories. You can also pass --rebase, --no-rebase,
подсказка: or --ff-only on the command line to override the configured default per
подсказка: invocation.
fatal: Need to specify how to reconcile divergent branches.
marialuneva@1511:~/marlinez/workspace/lab08$ git config pull.rebase false
marialuneva@1511:~/marlinez/workspace/lab08$ git pull origin master --no-rebase
Из https://github.com/marlinez/lab08
 * branch            master     -> FETCH_HEAD
fatal: отказ слияния несвязанных историй изменений
marialuneva@1511:~/marlinez/workspace/lab08$ git pull origin master --allow-unrelated-histories
Из https://github.com/marlinez/lab08
 * branch            master     -> FETCH_HEAD
Автослияние LICENSE
КОНФЛИКТ (добавление/добавление): Конфликт слияния в LICENSE
Автослияние README.md
КОНФЛИКТ (добавление/добавление): Конфликт слияния в README.md
Сбой автоматического слияния; исправьте конфликты, затем зафиксируйте результат.
marialuneva@1511:~/marlinez/workspace/lab08$ git add README.md
marialuneva@1511:~/marlinez/workspace/lab08$ git add LICENSE
marialuneva@1511:~/marlinez/workspace/lab08$ git pull origin master --allow-unrelated-histories
error: Вы не завершили слияние (присутствует файл MERGE_HEAD).
подсказка: Перед слиянием, выполните коммит ваших изменений.
fatal: Выход из-за незавершенного слияния.
marialuneva@1511:~/marlinez/workspace/lab08$ git commit
[master e65a2c6] Merge branch 'master' of https://github.com/marlinez/lab08
marialuneva@1511:~/marlinez/workspace/lab08$ git pull origin master --allow-unrelated-histories
Из https://github.com/marlinez/lab08
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/lab08$ git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	demo/

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
marialuneva@1511:~/marlinez/workspace/lab08$ git add .
marialuneva@1511:~/marlinez/workspace/lab08$ git status
Текущая ветка: master
Изменения, которые будут включены в коммит:
  (используйте «git restore --staged <файл>...», чтобы убрать из индекса)
	новый файл:    demo/main.cpp

marialuneva@1511:~/marlinez/workspace/lab08$ cat > Dockerfile <<EOF
> FROM ubuntu:18.04
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> RUN apt update
RUN apt install -yy gcc g++ cmake
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> COPY . print/
WORKDIR print
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> ENV LOG_PATH /home/logs/log.txt
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> VOLUME /home/logs
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> WORKDIR _install/bin
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ cat >> Dockerfile <<EOF
> ENTRYPOINT ./demo
EOF
marialuneva@1511:~/marlinez/workspace/lab08$ docker build -t logger .
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/

Sending build context to Docker daemon  28.32MB
Step 1/12 : FROM ubuntu:18.04
 ---> f9a80a55f492
Step 2/12 : RUN apt update
 ---> Using cache
 ---> cfd97e6a5f59
Step 3/12 : RUN apt install -yy gcc g++ cmake
 ---> Using cache
 ---> c5cd835f2411
Step 4/12 : COPY . print/
 ---> 5dfecb11b442
Step 5/12 : WORKDIR print
 ---> Running in 72cc3aab934e
 ---> Removed intermediate container 72cc3aab934e
 ---> 51e410766792
Step 6/12 : RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
 ---> Running in d3e7cdbde77f
CMake Error: The current CMakeCache.txt directory /print/_build/CMakeCache.txt is different than the directory /home/marialuneva/marlinez/workspace/projects/lab05/_build where CMakeCache.txt was created. This may result in binaries being created in the wrong place. If you are not sure, reedit the CMakeCache.txt
CMake Error: The source "/print/CMakeLists.txt" does not match the source "/home/marialuneva/marlinez/workspace/projects/lab05/CMakeLists.txt" used to generate cache.  Re-run cmake with a different source directory.
The command '/bin/sh -c cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install' returned a non-zero code: 1
marialuneva@1511:~/marlinez/workspace/lab08$ docker build -t logger .
DEPRECATED: The legacy builder is deprecated and will be removed in a future release.
            Install the buildx component to build images with BuildKit:
            https://docs.docker.com/go/buildx/

Sending build context to Docker daemon  28.32MB
Step 1/13 : FROM ubuntu:18.04
 ---> f9a80a55f492
Step 2/13 : RUN apt update
 ---> Using cache
 ---> cfd97e6a5f59
Step 3/13 : RUN apt install -yy gcc g++ cmake
 ---> Using cache
 ---> c5cd835f2411
Step 4/13 : COPY . print/
 ---> 06e15ffc61d9
Step 5/13 : WORKDIR print
 ---> Running in 2c63b4488af4
 ---> Removed intermediate container 2c63b4488af4
 ---> 9215f543774b
Step 6/13 : RUN rm -rf _build && mkdir _build && cd _build && cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
 ---> Running in d5615e5a5a69
-- The C compiler identification is GNU 7.5.0
-- The CXX compiler identification is GNU 7.5.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /print/_build
 ---> Removed intermediate container d5615e5a5a69
 ---> f854bc2f05f7
Step 7/13 : RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
 ---> Running in 98b270495555
-- Configuring done
-- Generating done
-- Build files have been written to: /print/_build
 ---> Removed intermediate container 98b270495555
 ---> 08b5015f2a58
Step 8/13 : RUN cmake --build _build
 ---> Running in 047d6721ed57
Scanning dependencies of target print
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
 ---> Removed intermediate container 047d6721ed57
 ---> f276aa7e76eb
Step 9/13 : RUN cmake --build _build --target install
 ---> Running in 3ffacbbe8043
[100%] Built target print
Install the project...
-- Install configuration: "Release"
-- Installing: /print/_install/lib/libprint.a
-- Installing: /print/_install/include
-- Installing: /print/_install/include/print.hpp
-- Installing: /print/_install/cmake/print-config.cmake
-- Installing: /print/_install/cmake/print-config-release.cmake
 ---> Removed intermediate container 3ffacbbe8043
 ---> a0b1c15f100f
Step 10/13 : ENV LOG_PATH /home/logs/log.txt
 ---> Running in 5633fc81aa7b
 ---> Removed intermediate container 5633fc81aa7b
 ---> 713e503cf4d3
Step 11/13 : VOLUME /home/logs
 ---> Running in e720e335c8ad
 ---> Removed intermediate container e720e335c8ad
 ---> 7288be19e93c
Step 12/13 : WORKDIR _install/bin
 ---> Running in 2c74fe6e1aa1
 ---> Removed intermediate container 2c74fe6e1aa1
 ---> df24bbdb5eed
Step 13/13 : ENTRYPOINT ./demo
 ---> Running in 06edac1ed11b
 ---> Removed intermediate container 06edac1ed11b
 ---> 20126f150237
Successfully built 20126f150237
Successfully tagged logger:latest
marialuneva@1511:~/marlinez/workspace/lab08$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
logger       latest    20126f150237   9 seconds ago        362MB
<none>       <none>    51e410766792   About a minute ago   361MB
<none>       <none>    6b28e05c1b9a   33 hours ago         362MB
<none>       <none>    ea40c8bc5311   33 hours ago         361MB
<none>       <none>    960236b43000   5 days ago           389MB
<none>       <none>    c45d0748fc75   5 days ago           361MB
<none>       <none>    c2a44950ccf7   5 days ago           361MB
<none>       <none>    f7dd0193048e   5 days ago           361MB
<none>       <none>    3b8068b2a147   5 days ago           361MB
<none>       <none>    867d510f5d60   5 days ago           361MB
ubuntu       18.04     f9a80a55f492   23 months ago        63.2MB
marialuneva@1511:~/marlinez/workspace/lab08$ mkdir logs
marialuneva@1511:~/marlinez/workspace/lab08$ docker run -it -v "$(pwd)/logs/:/home/logs/" logger
/bin/sh: 1: ./demo: not found
marialuneva@1511:~/marlinez/workspace/lab08$ docker inspect logger
[
    {
        "Id": "sha256:20126f150237c1bcb977fc6f738db1b8f772d598aad5b8c8e8962db8044b8206",
        "RepoTags": [
            "logger:latest"
        ],
        "RepoDigests": [],
        "Parent": "sha256:df24bbdb5eed91b260831c160adcea15e70a37c17dbc167609c5e7d81718fcb9",
        "Comment": "",
        "Created": "2025-04-25T17:35:47.296395459Z",
        "DockerVersion": "27.5.1",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "LOG_PATH=/home/logs/log.txt"
            ],
            "Cmd": null,
            "Image": "sha256:df24bbdb5eed91b260831c160adcea15e70a37c17dbc167609c5e7d81718fcb9",
            "Volumes": {
                "/home/logs": {}
            },
            "WorkingDir": "/print/_install/bin",
            "Entrypoint": [
                "/bin/sh",
                "-c",
                "./demo"
            ],
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "18.04"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 361681606,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/snap/docker/common/var-lib-docker/overlay2/8cf71f6fdc5484c70b325cfe79a07bc405438965175bd279e05c934e8ff51708/diff:/var/snap/docker/common/var-lib-docker/overlay2/97292f72361f8556b7e14068b37e14cc53f731f4308c4786cd0a73cf3d1f6a03/diff:/var/snap/docker/common/var-lib-docker/overlay2/421b75ea2d7cd6ab201171f9be8ddcf7010de045eedc061ff8e1690a9d92e6c4/diff:/var/snap/docker/common/var-lib-docker/overlay2/6de7465bc91cb53801e9aef6a4acf4e5961c72b8bf9612eb952d0b4a7a9a8c41/diff:/var/snap/docker/common/var-lib-docker/overlay2/55d73ac596c91d36e19f9639c680b33871335473cb2b68e81221082c1ea4602f/diff:/var/snap/docker/common/var-lib-docker/overlay2/e106e510d7397509ad2f13be87068a2f25bc486723e42a931351cef1e999858c/diff:/var/snap/docker/common/var-lib-docker/overlay2/6aff6fda6c4190f7a64ff542a1e0f54281e97be8d7ce05afba34a23b812119cf/diff:/var/snap/docker/common/var-lib-docker/overlay2/c9dfab939b20d808bc94bf60f8ffe72bd312bd22d0fd37e653d0e81bc8851f46/diff",
                "MergedDir": "/var/snap/docker/common/var-lib-docker/overlay2/40ad4d7dab83632f6ca828b217bde67b99e4c0d2c5514c1ed9f83ab44a613cc5/merged",
                "UpperDir": "/var/snap/docker/common/var-lib-docker/overlay2/40ad4d7dab83632f6ca828b217bde67b99e4c0d2c5514c1ed9f83ab44a613cc5/diff",
                "WorkDir": "/var/snap/docker/common/var-lib-docker/overlay2/40ad4d7dab83632f6ca828b217bde67b99e4c0d2c5514c1ed9f83ab44a613cc5/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:548a79621a426b4eb077c926eabac5a8620c454fb230640253e1b44dc7dd7562",
                "sha256:183fa34f5cd61738a42eef0b4158fc0d9bb07f5ada402055fc4306b0d4e0ec02",
                "sha256:0d80c860895c2b759853976d885b3cec8ba055afbe2eb58d9e0eab6f86f36a34",
                "sha256:89a79d1aee69bb9dae3de358e017af94b9222557dde8f83b7d5bdd838f3dcea1",
                "sha256:bd6fa67fc3c7fb3606b9bcb9950ef09d05ea4852da209553e0e9fac816393fde",
                "sha256:724f08d635d93ab3dfaac35859bd80d435c6b7c91796c4ef988d43fd7c4baf48",
                "sha256:0731b4462daab575a169261277c11bb998afe2f2b25b049e935f0ed945615665",
                "sha256:26fd4ecaac878a7957becaa79b3ae5fd1d79b99bbd241d3ce1880bf328199a60",
                "sha256:3d3c816d493cdff0b173743a5860cf22b031f92058cdb4bfc2b22cba0f6b0697"
            ]
        },
        "Metadata": {
            "LastTagTime": "2025-04-25T20:35:47.31901681+03:00"
        }
    }
]
marialuneva@1511:~/marlinez/workspace/lab08$ cat logs/log.txt
cat: logs/log.txt: Нет такого файла или каталога
marialuneva@1511:~/marlinez/workspace/lab08$ mkdir -p logs
marialuneva@1511:~/marlinez/workspace/lab08$ touch logs/log.txt
marialuneva@1511:~/marlinez/workspace/lab08$ cat logs/log.txt
text1
text2
text3
<C-D>
marialuneva@1511:~/marlinez/workspace/lab08$ gsed -i 's/lab07/lab08/g' README.md
Команда «gsed» не найдена. Возможно, вы имели в виду:
  команда 'gsad' из deb-пакета gsad (22.8.0-1)
  команда 'msed' из deb-пакета mblaze (1.1-1)
  команда 'gsec' из deb-пакета firebird3.0-utils (3.0.11.33637.ds4-2ubuntu2)
  команда 'gsd' из deb-пакета python3-gsd (3.0.1-3build1)
  команда 'gsnd' из deb-пакета ghostscript (10.02.1~dfsg1-0ubuntu7.5)
  команда 'sed' из deb-пакета sed (4.9-2)
  команда 'gted' из deb-пакета gnome-text-editor (46.3-0ubuntu2)
  команда 'ssed' из deb-пакета ssed (3.62-8)
Попробуйте: sudo apt install <имя_deb-пакета>
marialuneva@1511:~/marlinez/workspace/lab08$ sed -i 's/lab07/lab08/g' README.md
marialuneva@1511:~/marlinez/workspace/lab08$ vim .travis.yml
marialuneva@1511:~/marlinez/workspace/lab08$ git add Dockerfile
marialuneva@1511:~/marlinez/workspace/lab08$ git add .travis.yml
marialuneva@1511:~/marlinez/workspace/lab08$ git commit -m"adding Dockerfile"
[master 3ffd4e2] adding Dockerfile
 2 files changed, 33 insertions(+)
 create mode 100644 Dockerfile
 create mode 100644 demo/main.cpp
marialuneva@1511:~/marlinez/workspace/lab08$ git push origin master
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 241, готово.
Подсчет объектов: 100% (241/241), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (123/123), готово.
Запись объектов: 100% (238/238), 1.03 МиБ | 117.06 МиБ/с, готово.
Всего 238 (изменений 91), повторно использовано 226 (изменений 86), повторно использовано пакетов 0
remote: Resolving deltas: 100% (91/91), completed with 1 local object.
remote: error: GH013: Repository rule violations found for refs/heads/master.
remote: 
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote: 
remote:     - Push cannot contain secrets
remote: 
remote:     
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 31d495b283be4377cf3386913b7508723987afa2
remote:            path: README.md:2
remote:          - commit: 3af7f9fb2e49ba4888990b79fa085cd0e1d89383
remote:            path: README.md:2
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/marlinez/lab08/security/secret-scanning/unblock-secret/2wEO3pOdce1xgomf5XoOkx6AFpB
remote:     
remote: 
remote: 
To https://github.com/marlinez/lab08
 ! [remote rejected] master -> master (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «https://github.com/marlinez/lab08»
marialuneva@1511:~/marlinez/workspace/lab08$ git push origin master
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 241, готово.
Подсчет объектов: 100% (241/241), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (123/123), готово.
Запись объектов: 100% (238/238), 1.03 МиБ | 131.69 МиБ/с, готово.
Всего 238 (изменений 91), повторно использовано 226 (изменений 86), повторно использовано пакетов 0
remote: Resolving deltas: 100% (91/91), completed with 1 local object.
To https://github.com/marlinez/lab08
   f826c40..3ffd4e2  master -> master
marialuneva@1511:~/marlinez/workspace/lab08$ 

