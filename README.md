marialuneva@1511:~$ export GITHUB_USERNAME=marlinez
marialuneva@1511:~$ export GITHUB_EMAIL=maria15lun@mail.ru
marialuneva@1511:~$ alias edit=nano
marialuneva@1511:~$ alias gsed=sed
marialuneva@1511:~$ cd ${GITHUB_USERNAME}/workspace
marialuneva@1511:~/marlinez/workspace$ pushd .
~/marlinez/workspace ~/marlinez/workspace
marialuneva@1511:~/marlinez/workspace$ source scripts/activate
marialuneva@1511:~/marlinez/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab05 projects/lab06
Клонирование в «projects/lab06»...
remote: Enumerating objects: 199, done.
remote: Counting objects: 100% (199/199), done.
remote: Compressing objects: 100% (107/107), done.
remote: Total 199 (delta 70), reused 192 (delta 68), pack-reused 0 (from 0)
Получение объектов: 100% (199/199), 1.00 МиБ | 1.25 МиБ/с, готово.
Определение изменений: 100% (70/70), готово.
marialuneva@1511:~/marlinez/workspace$ cd projects/lab06
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git remote remove origin
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab06
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (4/4), 4.73 КиБ | 4.73 МиБ/с, готово.
Из https://github.com/marlinez/lab06
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
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git config pull.rebase false
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git pull origin master
Из https://github.com/marlinez/lab06
 * branch            master     -> FETCH_HEAD
fatal: отказ слияния несвязанных историй изменений
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git pull origin master --allow-unrelated-histories
Из https://github.com/marlinez/lab06
 * branch            master     -> FETCH_HEAD
Автослияние LICENSE
КОНФЛИКТ (добавление/добавление): Конфликт слияния в LICENSE
Автослияние README.md
КОНФЛИКТ (добавление/добавление): Конфликт слияния в README.md
Сбой автоматического слияния; исправьте конфликты, затем зафиксируйте результат.
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git add .
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git commit -m "Объединение независимых историй"
[master 67dfb08] Объединение независимых историй
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git pull origin master
Из https://github.com/marlinez/lab06
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_STRING "v\${PRINT_VERSION}")
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION\
  \${PRINT_VERSION_MAJOR}.\${PRINT_VERSION_MINOR}.\${PRINT_VERSION_PATCH}.\${PRINT_VERSION_TWEAK})
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_TWEAK 0)
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_PATCH 0)
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_MINOR 1)
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_MAJOR 0)
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git diff
diff --git a/CMakeLists.txt b/CMakeLists.txt
index 89739e7..7497219 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -7,6 +7,13 @@ option(BUILD_EXAMPLES "Build examples" OFF)
 option(BUILD_TESTS "Build tests" OFF)
 
 project(print)
+set(PRINT_VERSION_MAJOR 0)
+set(PRINT_VERSION_MINOR 1)
+set(PRINT_VERSION_PATCH 0)
+set(PRINT_VERSION_TWEAK 0)
+set(PRINT_VERSION
+  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})
+set(PRINT_VERSION_STRING "v${PRINT_VERSION}")
 
 add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
 
marialuneva@1511:~/marlinez/workspace/projects/lab06$ touch DESCRIPTION && edit DESCRIPTION
marialuneva@1511:~/marlinez/workspace/projects/lab06$ touch ChangeLog.md
marialuneva@1511:~/marlinez/workspace/projects/lab06$ export DATE="`LANG=en_US date +'%a %b %d %Y'`"
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat > ChangeLog.md <<EOF
> cat > ChangeLog.md <<EOF
> 
> include(InstallRequiredSystemLibraries)
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git add ChangeLog.md
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> set(CPACK_PACKAGE_CONTACT ${GITHUB_EMAIL})
set(CPACK_PACKAGE_VERSION_MAJOR \${PRINT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR \${PRINT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH \${PRINT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION_TWEAK \${PRINT_VERSION_TWEAK})
set(CPACK_PACKAGE_VERSION \${PRINT_VERSION})
set(CPACK_PACKAGE_DESCRIPTION_FILE \${CMAKE_CURRENT_SOURCE_DIR}/DESCRIPTION)
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "static C++ library for printing")
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> set(CPACK_RESOURCE_FILE_LICENSE \${CMAKE_CURRENT_SOURCE_DIR}/LICENSE)
set(CPACK_RESOURCE_FILE_README \${CMAKE_CURRENT_SOURCE_DIR}/README.md)
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> set(CPACK_RPM_PACKAGE_NAME "print-devel")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")
set(CPACK_RPM_PACKAGE_GROUP "print")
set(CPACK_RPM_CHANGELOG_FILE \${CMAKE_CURRENT_SOURCE_DIR}/ChangeLog.md)
set(CPACK_RPM_PACKAGE_RELEASE 1)
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> set(CPACK_DEBIAN_PACKAGE_NAME "libprint-dev")
set(CPACK_DEBIAN_PACKAGE_PREDEPENDS "cmake >= 3.0")
set(CPACK_DEBIAN_PACKAGE_RELEASE 1)
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> include(CPack)
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cat >> CMakeLists.txt <<EOF
> include(CPackConfig.cmake)
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab06$ gsed -i 's/lab05/lab06/g' README.md
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git add .
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git commit -m"added cpack config"
[master e70282a] added cpack config
 5 files changed, 110 insertions(+), 80 deletions(-)
 create mode 100644 CPackConfig.cmake
 create mode 100644 ChangeLog.md
 create mode 100644 DESCRIPTION
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git tag v0.1.0.0
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git pull origin master
Из https://github.com/marlinez/lab06
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git push origin master --tags
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 216, готово.
Подсчет объектов: 100% (216/216), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (117/117), готово.
Запись объектов: 100% (213/213), 1.00 МиБ | 68.50 МиБ/с, готово.
Всего 213 (изменений 80), повторно использовано 194 (изменений 70), повторно использовано пакетов 0
remote: Resolving deltas: 100% (80/80), completed with 1 local object.
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
remote:        https://github.com/marlinez/lab06/security/secret-scanning/unblock-secret/2v88zXxfnbBvGZkfnD6l6QAZpx1
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
remote:        https://github.com/marlinez/lab06/security/secret-scanning/unblock-secret/2v88zXxfnbBvGZkfnD6l6QAZpx1
remote:     
remote: 
remote: 
To https://github.com/marlinez/lab06
 ! [remote rejected] master -> master (push declined due to repository rule violations)
 ! [remote rejected] v0.1.0.0 -> v0.1.0.0 (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «https://github.com/marlinez/lab06»
marialuneva@1511:~/marlinez/workspace/projects/lab06$ git push origin master --tags
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 216, готово.
Подсчет объектов: 100% (216/216), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (117/117), готово.
Запись объектов: 100% (213/213), 1.00 МиБ | 102.76 МиБ/с, готово.
Всего 213 (изменений 80), повторно использовано 194 (изменений 70), повторно использовано пакетов 0
remote: Resolving deltas: 100% (80/80), completed with 1 local object.
To https://github.com/marlinez/lab06
   78cb4d4..e70282a  master -> master
 * [new tag]         v0.1.0.0 -> v0.1.0.0
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cmake -H. -B_build
CMake Error: The current CMakeCache.txt directory /home/marialuneva/marlinez/workspace/projects/lab06/_build/CMakeCache.txt is different than the directory /home/marialuneva/marlinez/workspace/projects/lab05/_build where CMakeCache.txt was created. This may result in binaries being created in the wrong place. If you are not sure, reedit the CMakeCache.txt
CMake Error: The source "/home/marialuneva/marlinez/workspace/projects/lab06/CMakeLists.txt" does not match the source "/home/marialuneva/marlinez/workspace/projects/lab05/CMakeLists.txt" used to generate cache.  Re-run cmake with a different source directory.
marialuneva@1511:~/marlinez/workspace/projects/lab06$ rm -rf _build
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cmake -H. -B_build
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
-- Configuring done (0.4s)
-- Generating done (0.0s)
-- Build files have been written to: /home/marialuneva/marlinez/workspace/projects/lab06/_build
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cd _build
marialuneva@1511:~/marlinez/workspace/projects/lab06/_build$ cpack -G "TGZ"
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/marialuneva/marlinez/workspace/projects/lab06/_build/print-0.1.0.0-Linux.tar.gz generated.
marialuneva@1511:~/marlinez/workspace/projects/lab06/_build$ cd ..
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/marialuneva/marlinez/workspace/projects/lab06/_build
marialuneva@1511:~/marlinez/workspace/projects/lab06$ cmake --build _build --target package
[100%] Built target print
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/marialuneva/marlinez/workspace/projects/lab06/_build/print-0.1.0.0-Linux.tar.gz generated.
marialuneva@1511:~/marlinez/workspace/projects/lab06$ mkdir artifacts
marialuneva@1511:~/marlinez/workspace/projects/lab06$ mv _build/*.tar.gz artifacts
marialuneva@1511:~/marlinez/workspace/projects/lab06$ tree artifacts
artifacts
└── print-0.1.0.0-Linux.tar.gz

1 directory, 1 file
marialuneva@1511:~/marlinez/workspace/projects/lab06$ 

# lab07

