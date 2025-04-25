marialuneva@1511:~$ export GITHUB_TOKEN=<token>
marialuneva@1511:~$ export GITHUB_USERNAME=marlinez
marialuneva@1511:~$ export PACKAGE_MANAGER=apt
marialuneva@1511:~$ export GPG_PACKAGE_NAME=gpg
marialuneva@1511:~$ $PACKAGE_MANAGER install xclip
E: Не удалось открыть файл блокировки /var/lib/dpkg/lock-frontend - open (13: Отказано в доступе)
E: Невозможно получить блокировку внешнего интерфейса dpkg (/var/lib/dpkg/lock-frontend); у вас есть права суперпользователя?
marialuneva@1511:~$ sudo $PACKAGE_MANAGER install xclip
[sudo] пароль для marialuneva: 
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Уже установлен пакет xclip самой новой версии (0.13-3).
Следующие пакеты устанавливались автоматически и больше не требуются:
  cpp-14 cpp-14-x86-64-linux-gnu g++-14 g++-14-x86-64-linux-gnu gcc-14 gcc-14-x86-64-linux-gnu gccgo-14
  gccgo-14-x86-64-linux-gnu libgcc-14-dev libgo-14-dev libgo23 libstdc++-14-dev
Для их удаления используйте «sudo apt autoremove».
Обновлено 0 пакетов, установлено 0 новых пакетов, для удаления отмечено 0 пакетов, и 103 пакетов не обновлено.
marialuneva@1511:~$ alias gsed=sed
marialuneva@1511:~$ alias pbcopy='xclip -selection clipboard'
marialuneva@1511:~$ alias pbpaste='xclip -selection clipboard -o'
marialuneva@1511:~$ cd ${GITHUB_USERNAME}/workspace
marialuneva@1511:~/marlinez/workspace$ pushd .
~/marlinez/workspace ~/marlinez/workspace
marialuneva@1511:~/marlinez/workspace$ source scripts/activate
marialuneva@1511:~/marlinez/workspace$ go get github.com/aktau/github-release
go: go.mod file not found in current directory or any parent directory.
	'go get' is no longer supported outside a module.
	To build and install a command, use 'go install' with a version,
	like 'go install example.com/cmd@latest'
	For more information, see https://golang.org/doc/go-get-install-deprecation
	or run 'go help get' or 'go help install'.
marialuneva@1511:~/marlinez/workspace$ go get github.com/aktau/github-release
go: go.mod file not found in current directory or any parent directory.
	'go get' is no longer supported outside a module.
	To build and install a command, use 'go install' with a version,
	like 'go install example.com/cmd@latest'
	For more information, see https://golang.org/doc/go-get-install-deprecation
	or run 'go help get' or 'go help install'.
marialuneva@1511:~/marlinez/workspace$ go install github.com/aktau/github-release@latest
go: downloading github.com/aktau/github-release v0.10.1
go: finding module for package github.com/voxelbrain/goptions
go: finding module for package github.com/dustin/go-humanize
go: finding module for package github.com/github-release/github-release/github
go: downloading github.com/dustin/go-humanize v1.0.1
go: downloading github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: downloading github.com/github-release/github-release v0.10.1
go: found github.com/dustin/go-humanize in github.com/dustin/go-humanize v1.0.1
go: found github.com/github-release/github-release/github in github.com/github-release/github-release v0.10.1
go: found github.com/voxelbrain/goptions in github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: finding module for package github.com/tomnomnom/linkheader
go: finding module for package github.com/kevinburke/rest/restclient
go: downloading github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80
go: downloading github.com/kevinburke/rest v0.0.0-20240617045629-3ed0ad3487f0
go: found github.com/kevinburke/rest/restclient in github.com/kevinburke/rest v0.0.0-20240617045629-3ed0ad3487f0
go: found github.com/tomnomnom/linkheader in github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80
marialuneva@1511:~/marlinez/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab08 projects/lab09
Клонирование в «projects/lab09»...
remote: Enumerating objects: 245, done.
remote: Counting objects: 100% (245/245), done.
remote: Compressing objects: 100% (124/124), done.
remote: Total 245 (delta 92), reused 238 (delta 91), pack-reused 0 (from 0)
Получение объектов: 100% (245/245), 1.04 МиБ | 1.45 МиБ/с, готово.
Определение изменений: 100% (92/92), готово.
marialuneva@1511:~/marlinez/workspace$ cd projects/lab09
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git remote remove origin
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab09
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git pull origin master
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (3/3), 851 байт | 851.00 КиБ/с, готово.
Из https://github.com/marlinez/lab09
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
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git config pull.rebase false
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git pull origin master --no-rebase
Из https://github.com/marlinez/lab09
 * branch            master     -> FETCH_HEAD
fatal: отказ слияния несвязанных историй изменений
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git pull origin master --allow-unrelated-histories
Из https://github.com/marlinez/lab09
 * branch            master     -> FETCH_HEAD
Автослияние README.md
КОНФЛИКТ (добавление/добавление): Конфликт слияния в README.md
Сбой автоматического слияния; исправьте конфликты, затем зафиксируйте результат.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git commit
[master acb40bc] Merge branch 'master' of https://github.com/marlinez/lab09
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git pull origin master --allow-unrelated-histories
Из https://github.com/marlinez/lab09
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git pull origin master
Из https://github.com/marlinez/lab09
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ sed -i 's/lab08/lab09/g' README.md
marialuneva@1511:~/marlinez/workspace/projects/lab09$ gpg --list-secret-keys --keyid-format LONG
/home/marialuneva/.gnupg/pubring.kbx
------------------------------------
sec   rsa3072/34CE29DC8F4DB656 2025-04-25 [SC] [годен до: 2026-04-25]
      B8242F70982A95365B0D69DC34CE29DC8F4DB656
uid               [  абсолютно ] maria <maria15lun@mail.ru>
ssb   rsa3072/2D8FCECE6F06B722 2025-04-25 [E] [годен до: 2026-04-25]

sec   rsa3072/5FE2CC8E69CB1D83 2025-04-25 [SC] [годен до: 2026-04-25]
      8CE0D9B81474BD0B09672F8B5FE2CC8E69CB1D83
uid               [  абсолютно ] marlinez <maria15lun@mail.ru>
ssb   rsa3072/C3BC7861B56631D6 2025-04-25 [E] [годен до: 2026-04-25]

marialuneva@1511:~/marlinez/workspace/projects/lab09$ gpg -K ${GITHUB_USERNAME}
sec   rsa3072 2025-04-25 [SC] [годен до: 2026-04-25]
      8CE0D9B81474BD0B09672F8B5FE2CC8E69CB1D83
uid         [  абсолютно ] marlinez <maria15lun@mail.ru>
ssb   rsa3072 2025-04-25 [E] [годен до: 2026-04-25]

marialuneva@1511:~/marlinez/workspace/projects/lab09$ GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
marialuneva@1511:~/marlinez/workspace/projects/lab09$ gpg --armor --export ${GPG_KEY_ID} | pbcopy
marialuneva@1511:~/marlinez/workspace/projects/lab09$ pbpaste
pbpastemarialuneva@1511:~/marlinez/workspace/projects/lab09$ open https://github.com/settings/keys
marialuneva@1511:~/marlinez/workspace/projects/lab09$ Gtk-Message: 21:26:12.980: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
git config user.signingkey ${GPG_SEC_KEY_ID}
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git config user.signingkey ${GPG_SEC_KEY_ID}
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git config gpg.program gpg
marialuneva@1511:~/marlinez/workspace/projects/lab09$ test -r ~/.bash_profile && echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile
marialuneva@1511:~/marlinez/workspace/projects/lab09$ echo 'export GPG_TTY=$(tty)' >> ~/.profile
marialuneva@1511:~/marlinez/workspace/projects/lab09$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
CMake Error: The current CMakeCache.txt directory /home/marialuneva/marlinez/workspace/projects/lab09/_build/CMakeCache.txt is different than the directory /home/marialuneva/marlinez/workspace/projects/lab05/_build where CMakeCache.txt was created. This may result in binaries being created in the wrong place. If you are not sure, reedit the CMakeCache.txt
CMake Error: The source "/home/marialuneva/marlinez/workspace/projects/lab09/CMakeLists.txt" does not match the source "/home/marialuneva/marlinez/workspace/projects/lab05/CMakeLists.txt" used to generate cache.  Re-run cmake with a different source directory.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ rm -rf _build
marialuneva@1511:~/marlinez/workspace/projects/lab09$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.3s)
-- Generating done (0.0s)
-- Build files have been written to: /home/marialuneva/marlinez/workspace/projects/lab09/_build
marialuneva@1511:~/marlinez/workspace/projects/lab09$ cmake --build _build --target package
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/marialuneva/marlinez/workspace/projects/lab09/_build/print-0.1.0.0-Linux.tar.gz generated.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ travis login --auto
Команда «travis» не найдена, но может быть установлена с помощью:
sudo snap install travis  # version 1.8.9, or
sudo apt  install travis  # version 220729-1
См. 'snap info travis', чтобы посмотреть дополнительные версии.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git tag -s v0.1.0.0 -m "Initial release"
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git tag -v v0.1.0.0
object acb40bcc544f88c9079c3b6f03d721bceb1d30b8
type commit
tag v0.1.0.0
tagger marlinez <maria15lun@mail.ru> 1745605914 +0300

Initial release
gpg: Подпись сделана Пт 25 апр 2025 21:31:54 MSK
gpg:                ключом RSA с идентификатором 8CE0D9B81474BD0B09672F8B5FE2CC8E69CB1D83
gpg: Действительная подпись пользователя "marlinez <maria15lun@mail.ru>" [абсолютное]
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git show v0.1.0.0
tag v0.1.0.0
Tagger: marlinez <maria15lun@mail.ru>
Date:   Fri Apr 25 21:31:54 2025 +0300

Initial release
-----BEGIN PGP SIGNATURE-----

iQGzBAABCgAdFiEEjODZuBR0vQsJZy+LX+LMjmnLHYMFAmgL1RoACgkQX+LMjmnL
HYPqjQwAxbcaGxZW8Yxp290DBU3eLm8kQSr78YUhJZVpGKOjZe+MDdtK7POyZtKd
9zWs3Pa3K0rcOn1k5OS5qtLOG+gTf23m9Lu6zxBDbXDYkZPn49iNuEeWNOWRm3gK
lGGJ6tQgrtICiDag98Fx11C5h81sHJUuwSzaO9dgWQwINBf7wBQ/z/WXUOcPF6gF
aJ1bC1jNGM6WSsKYbLIUe/32u1iGPoO1J6PhG/RXnwVxNVc3NAlotaYpP8anr5fn
bA24h5kIPxyD5hER+0WBd1Rnd4wy9xO1SA0ll/X70SeNmRxbuMvJHQbfmGkQ2tMx
ZDnWaSgL43LnXlAb7o4ni8dOBgERXwOGnslSBmm5pE/DvHvqOV5SrI5iOf5SiXmE
yh4/0F7gyg8lJTrmDHUB2rZzWf2TvdZe8pgoXzH3oErZKGaePJxqo69H5vEJiX8k
jmP1sm7CDjssVYy9qS/yU87Wh4TbqTcwZaHLyBU6kD7jbWt86BIoHZV9Osf88KVn
nw04dUuz
=3qZG
-----END PGP SIGNATURE-----

commit acb40bcc544f88c9079c3b6f03d721bceb1d30b8 (HEAD -> master, tag: v0.1.0.0)
Merge: 2b4c92b eddf7a4
Author: marlinez <maria15lun@mail.ru>
Date:   Fri Apr 25 21:23:18 2025 +0300

    Merge branch 'master' of https://github.com/marlinez/lab09

diff --cc README.md
index 096dd70,134733f..1414dea
--- a/README.md
+++ b/README.md
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git push origin master --tags
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 251, готово.
Подсчет объектов: 100% (251/251), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (127/127), готово.
Запись объектов: 100% (249/249), 1.04 МиБ | 118.51 МиБ/с, готово.
Всего 249 (изменений 94), повторно использовано 243 (изменений 92), повторно использовано пакетов 0
remote: Resolving deltas: 100% (94/94), done.
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
remote:        https://github.com/marlinez/lab09/security/secret-scanning/unblock-secret/2wEU9rh6Md3pWm65iPRgX3iXELV
remote:     
remote: 
remote: 
remote: error: GH013: Repository rule violations found for refs/tags/v0.1.0.0.
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
remote:        https://github.com/marlinez/lab09/security/secret-scanning/unblock-secret/2wEU9rh6Md3pWm65iPRgX3iXELV
remote:     
remote: 
remote: 
To https://github.com/marlinez/lab09
 ! [remote rejected] master -> master (push declined due to repository rule violations)
 ! [remote rejected] v0.1.0.0 -> v0.1.0.0 (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «https://github.com/marlinez/lab09»
marialuneva@1511:~/marlinez/workspace/projects/lab09$ git push origin master --tags
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 251, готово.
Подсчет объектов: 100% (251/251), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (127/127), готово.
Запись объектов: 100% (249/249), 1.04 МиБ | 106.66 МиБ/с, готово.
Всего 249 (изменений 94), повторно использовано 243 (изменений 92), повторно использовано пакетов 0
remote: Resolving deltas: 100% (94/94), done.
To https://github.com/marlinez/lab09
   eddf7a4..acb40bc  master -> master
 * [new tag]         v0.1.0.0 -> v0.1.0.0
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release --version
github-release: команда не найдена
marialuneva@1511:~/marlinez/workspace/projects/lab09$ go install github.com/aktau/github-release@latest
go: finding module for package github.com/dustin/go-humanize
go: finding module for package github.com/voxelbrain/goptions
go: finding module for package github.com/github-release/github-release/github
go: found github.com/dustin/go-humanize in github.com/dustin/go-humanize v1.0.1
go: found github.com/github-release/github-release/github in github.com/github-release/github-release v0.10.1
go: found github.com/voxelbrain/goptions in github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: finding module for package github.com/tomnomnom/linkheader
go: finding module for package github.com/kevinburke/rest/restclient
go: found github.com/kevinburke/rest/restclient in github.com/kevinburke/rest v0.0.0-20240617045629-3ed0ad3487f0
go: found github.com/tomnomnom/linkheader in github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release --version
github-release: команда не найдена
marialuneva@1511:~/marlinez/workspace/projects/lab09$ ls $(go env GOPATH)/bin/github-release
/home/marialuneva/go/bin/github-release
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release --version
github-release: команда не найдена
marialuneva@1511:~/marlinez/workspace/projects/lab09$ sudo apt update
[sudo] пароль для marialuneva: 
Сущ:1 http://ru.archive.ubuntu.com/ubuntu noble InRelease
Пол:2 http://ru.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Пол:3 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB] 
Пол:4 http://ru.archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Пол:5 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [1 027 kB]
Пол:6 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [782 kB]
Пол:7 http://ru.archive.ubuntu.com/ubuntu noble-updates/main Translation-en [223 kB]
Пол:8 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [161 kB]          
Пол:9 http://ru.archive.ubuntu.com/ubuntu noble-updates/main Icons (48x48) [34,7 kB]                
Пол:10 http://ru.archive.ubuntu.com/ubuntu noble-updates/main Icons (64x64) [49,6 kB]                  
Пол:11 http://ru.archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [964 kB]
Пол:12 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [147 kB]              
Пол:13 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components [21,6 kB]
Пол:14 http://security.ubuntu.com/ubuntu noble-security/main Icons (48x48) [13,4 kB]                    
Пол:15 http://security.ubuntu.com/ubuntu noble-security/main Icons (64x64) [20,0 kB]                      
Пол:16 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Packages [931 kB]          
Пол:17 http://security.ubuntu.com/ubuntu noble-security/restricted Translation-en [190 kB]          
Пол:18 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Components [212 B]      
Пол:19 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [834 kB]
Пол:20 http://ru.archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [198 kB]                            
Пол:21 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [181 kB]                               
Пол:22 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components [52,2 kB]                            
Пол:23 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Components [212 B]                            
Пол:24 http://ru.archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Components [212 B]                           
Пол:25 http://ru.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [1 057 kB]                            
Пол:26 http://ru.archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [267 kB]                              
Пол:27 http://ru.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [368 kB]                            
Пол:28 http://ru.archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]                           
Пол:29 http://ru.archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [7 088 B]                             
Пол:30 http://ru.archive.ubuntu.com/ubuntu noble-backports/restricted amd64 Components [216 B]                         
Пол:31 http://ru.archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [16,4 kB]                         
Пол:32 http://ru.archive.ubuntu.com/ubuntu noble-backports/universe Icons (48x48) [20,4 kB]                            
Пол:33 http://ru.archive.ubuntu.com/ubuntu noble-backports/universe Icons (64x64) [28,7 kB]                            
Пол:34 http://ru.archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Components [212 B]                         
Получено 7 974 kB за 10с (802 kB/s)                                                                                    
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Может быть обновлено 111 пакетов. Запустите «apt list --upgradable» для их показа.
marialuneva@1511:~/marlinez/workspace/projects/lab09$ sudo apt install github-release
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
E: Невозможно найти пакет github-release
marialuneva@1511:~/marlinez/workspace/projects/lab09$ ^[[200~sudo apt install golang~
sudo: команда не найдена
marialuneva@1511:~/marlinez/workspace/projects/lab09$ sudo apt install golang
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Следующие пакеты устанавливались автоматически и больше не требуются:
  cpp-14 cpp-14-x86-64-linux-gnu g++-14 g++-14-x86-64-linux-gnu gcc-14 gcc-14-x86-64-linux-gnu gccgo-14
  gccgo-14-x86-64-linux-gnu libgcc-14-dev libgo-14-dev libgo23 libstdc++-14-dev
Для их удаления используйте «sudo apt autoremove».
Будут установлены следующие дополнительные пакеты:
  golang-1.22 golang-1.22-doc golang-doc
Следующие НОВЫЕ пакеты будут установлены:
  golang golang-1.22 golang-1.22-doc golang-doc
Обновлено 0 пакетов, установлено 4 новых пакетов, для удаления отмечено 0 пакетов, и 111 пакетов не обновлено.
Необходимо скачать 118 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 678 kB.
Хотите продолжить? [Д/н] y
Пол:1 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 golang-1.22-doc all 1.22.2-2ubuntu0.3 [107 kB]
Пол:2 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 golang-1.22 all 1.22.2-2ubuntu0.3 [5 702 B]
Пол:3 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 golang-doc all 2:1.22~2build1 [2 788 B]
Пол:4 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 golang amd64 2:1.22~2build1 [2 736 B]
Получено 118 kB за 1с (188 kB/s)           
Выбор ранее не выбранного пакета golang-1.22-doc.
(Чтение базы данных … на данный момент установлено 220153 файла и каталога.)
Подготовка к распаковке …/golang-1.22-doc_1.22.2-2ubuntu0.3_all.deb …
Распаковывается golang-1.22-doc (1.22.2-2ubuntu0.3) …
Выбор ранее не выбранного пакета golang-1.22.
Подготовка к распаковке …/golang-1.22_1.22.2-2ubuntu0.3_all.deb …
Распаковывается golang-1.22 (1.22.2-2ubuntu0.3) …
Выбор ранее не выбранного пакета golang-doc.
Подготовка к распаковке …/golang-doc_2%3a1.22~2build1_all.deb …
Распаковывается golang-doc (2:1.22~2build1) …
Выбор ранее не выбранного пакета golang:amd64.
Подготовка к распаковке …/golang_2%3a1.22~2build1_amd64.deb …
Распаковывается golang:amd64 (2:1.22~2build1) …
Настраивается пакет golang-1.22-doc (1.22.2-2ubuntu0.3) …
Настраивается пакет golang-doc (2:1.22~2build1) …
Настраивается пакет golang-1.22 (1.22.2-2ubuntu0.3) …
Настраивается пакет golang:amd64 (2:1.22~2build1) …
marialuneva@1511:~/marlinez/workspace/projects/lab09$ go install github.com/aktau/github-release@latest
go: finding module for package github.com/voxelbrain/goptions
go: finding module for package github.com/dustin/go-humanize
go: finding module for package github.com/github-release/github-release/github
go: found github.com/dustin/go-humanize in github.com/dustin/go-humanize v1.0.1
go: found github.com/github-release/github-release/github in github.com/github-release/github-release v0.10.1
go: found github.com/voxelbrain/goptions in github.com/voxelbrain/goptions v0.0.0-20180630082107-58cddc247ea2
go: finding module for package github.com/tomnomnom/linkheader
go: finding module for package github.com/kevinburke/rest/restclient
go: found github.com/kevinburke/rest/restclient in github.com/kevinburke/rest v0.0.0-20240617045629-3ed0ad3487f0
go: found github.com/tomnomnom/linkheader in github.com/tomnomnom/linkheader v0.0.0-20180905144013-02ca5825eb80
marialuneva@1511:~/marlinez/workspace/projects/lab09$ echo 'export PATH="$PATH:$(go env GOPATH)/bin"' >> ~/.bashrc
marialuneva@1511:~/marlinez/workspace/projects/lab09$ source ~/.bashrc
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release --version
github-release v0.10.1
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release info -u ${GITHUB_USERNAME} -r lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/marlinez/lab09/commits/acb40bcc544f88c9079c3b6f03d721bceb1d30b8)
releases:
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release release \
> --user ${GITHUB_USERNAME} \
    --repo lab09 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"
marialuneva@1511:~/marlinez/workspace/projects/lab09$ export PACKAGE_OS=`uname -s` PACKAGE_ARCH=`uname -m`
marialuneva@1511:~/marlinez/workspace/projects/lab09$ export PACKAGE_FILENAME=print-${PACKAGE_OS}-${PACKAGE_ARCH}.tar.gz
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release upload \
> --user ${GITHUB_USERNAME} \
    --repo lab09 \
    --tag v0.1.0.0 \
    --name "${PACKAGE_FILENAME}" \
    --file _build/*.tar.gz
marialuneva@1511:~/marlinez/workspace/projects/lab09$ github-release info -u ${GITHUB_USERNAME} -r lab09
tags:
- v0.1.0.0 (commit: https://api.github.com/repos/marlinez/lab09/commits/acb40bcc544f88c9079c3b6f03d721bceb1d30b8)
releases:
- v0.1.0.0, name: 'libprint', description: 'my first release', id: 214860092, tagged: 25/04/2025 at 18:31, published: 25/04/2025 at 18:39, draft: ✗, prerelease: ✗
  - artifact: print-Linux-x86_64.tar.gz, downloads: 0, state: uploaded, type: application/octet-stream, size: 2.5 kB, id: 249513304
marialuneva@1511:~/marlinez/workspace/projects/lab09$ wget https://github.com/${GITHUB_USERNAME}/lab09/releases/download/v0.1.0.0/${PACKAGE_FILENAME}
--2025-04-25 21:41:06--  https://github.com/marlinez/lab09/releases/download/v0.1.0.0/print-Linux-x86_64.tar.gz
Распознаётся github.com (github.com)… 140.82.121.4
Подключение к github.com (github.com)|140.82.121.4|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 302 Found
Адрес: https://objects.githubusercontent.com/github-production-release-asset-2e65be/972811382/a7f3d038-a8c7-469c-83f2-a8b95bed6397?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250425%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250425T184106Z&X-Amz-Expires=300&X-Amz-Signature=63ddb20d0477a50e354a1f9abc9e7517d26e66db877066dfe0849027a4718909&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dprint-Linux-x86_64.tar.gz&response-content-type=application%2Foctet-stream [переход]
--2025-04-25 21:41:06--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/972811382/a7f3d038-a8c7-469c-83f2-a8b95bed6397?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250425%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250425T184106Z&X-Amz-Expires=300&X-Amz-Signature=63ddb20d0477a50e354a1f9abc9e7517d26e66db877066dfe0849027a4718909&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dprint-Linux-x86_64.tar.gz&response-content-type=application%2Foctet-stream
Распознаётся objects.githubusercontent.com (objects.githubusercontent.com)… 185.199.110.133, 185.199.108.133, 185.199.111.133, ...
Подключение к objects.githubusercontent.com (objects.githubusercontent.com)|185.199.110.133|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 2498 (2,4K) [application/octet-stream]
Сохранение в: ‘print-Linux-x86_64.tar.gz’

print-Linux-x86_64.tar.gz     100%[=================================================>]   2,44K  --.-KB/s    за 0,001s  

2025-04-25 21:41:07 (3,11 MB/s) - ‘print-Linux-x86_64.tar.gz’ сохранён [2498/2498]

marialuneva@1511:~/marlinez/workspace/projects/lab09$ tar -ztf ${PACKAGE_FILENAME}
print-0.1.0.0-Linux/lib/
print-0.1.0.0-Linux/lib/libprint.a
print-0.1.0.0-Linux/cmake/
print-0.1.0.0-Linux/cmake/print-config.cmake
print-0.1.0.0-Linux/cmake/print-config-noconfig.cmake
print-0.1.0.0-Linux/include/
print-0.1.0.0-Linux/include/print.hpp
