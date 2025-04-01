#lab05
marialuneva@1511:~$ export GITHUB_USERNAME=marlinez
marialuneva@1511:~$ export GITHUB_TOKEN=<token>
marialuneva@1511:~$ alias gsed=sed
marialuneva@1511:~$ cd ${GITHUB_USERNAME}/workspace
marialuneva@1511:~/marlinez/workspace$ pushd .
~/marlinez/workspace ~/marlinez/workspace
marialuneva@1511:~/marlinez/workspace$ source scripts/activate
marialuneva@1511:~/marlinez/workspace$ \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
Turning on ignore dotfiles mode.
Downloading https://github.com/rvm/rvm/archive/master.tar.gz
Upgrading the RVM installation in /home/marialuneva/.rvm/
Upgrade of RVM in /home/marialuneva/.rvm/ is complete.

Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.

👉  Donate: https://opencollective.com/rvm/donate


marialuneva@1511:~/marlinez/workspace$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
marialuneva@1511:~/marlinez/workspace$ . scripts/activate
marialuneva@1511:~/marlinez/workspace$ rvm autolibs disable
marialuneva@1511:~/marlinez/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab05
Клонирование в «projects/lab05»...
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 14 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Получение объектов: 100% (14/14), 5.51 КиБ | 5.51 МиБ/с, готово.
marialuneva@1511:~/marlinez/workspace$ cd projects/lab05
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git remote remove origin
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab05
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cat > .travis.yml <<EOF
> language: cpp
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cat >> .travis.yml <<EOF
> script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cat >> .travis.yml <<EOF
> addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab05$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add .travis.yml
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git commit -m"added CI"
[master 214b02c] added CI
 2 files changed, 13 insertions(+)
 create mode 100644 .travis.yml
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git config pull.rebase true
marialuneva@1511:~/marlinez/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab04 projects/lab05
Клонирование в «projects/lab05»...
remote: Enumerating objects: 22, done.
remote: Counting objects: 100% (22/22), done.
remote: Compressing objects: 100% (17/17), done.
remote: Total 22 (delta 3), reused 14 (delta 2), pack-reused 0 (from 0)
Получение объектов: 100% (22/22), 8.51 КиБ | 2.84 МиБ/с, готово.
Определение изменений: 100% (3/3), готово.
marialuneva@1511:~/marlinez/workspace$ cd projects/lab05
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git remote remove origin
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab05
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (4/4), 1.48 КиБ | 1.48 МиБ/с, готово.
Из https://github.com/marlinez/lab05
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
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git config pull.rebase false
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
fatal: отказ слияния несвязанных историй изменений
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master --allow-unrelated-histories
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
Автослияние README.md
КОНФЛИКТ (добавление/добавление): Конфликт слияния в README.md
error: не удалось применить коммит 8ea0a69... Add files via upload
подсказка: Resolve all conflicts manually, mark them as resolved with
подсказка: "git add/rm <conflicted_files>", then run "git rebase --continue".
подсказка: You can instead skip this commit: run "git rebase --skip".
подсказка: To abort and get back to the state before "git rebase", run "git rebase --abort".
Не удалось применить коммит 8ea0a69... Add files via upload
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git rebase --continue
[отделённый HEAD d0d1781] Add files via upload
 6 files changed, 243 insertions(+), 1 deletion(-)
 create mode 100644 CMakeLists.txt
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
Автослияние README.md
КОНФЛИКТ (содержимое): Конфликт слияния в README.md
error: не удалось применить коммит 214b02c... added CI
подсказка: Resolve all conflicts manually, mark them as resolved with
подсказка: "git add/rm <conflicted_files>", then run "git rebase --continue".
подсказка: You can instead skip this commit: run "git rebase --skip".
подсказка: To abort and get back to the state before "git rebase", run "git rebase --abort".
Не удалось применить коммит 214b02c... added CI
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git commit -m "Resolved merge conflicts"
[отделённый HEAD 5a01e80] Resolved merge conflicts
 2 files changed, 188 insertions(+)
 create mode 100644 .travis.yml
Сбой автоматического слияния; исправьте конфликты, затем зафиксируйте результат.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add .
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git commit -m "Объединение независимых историй"
[master 3af7f9f] Объединение независимых историй
>>>>>>> ae8d022f8cfc3d40042780bd20863b5f6aef4abc
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ mkdir third-party
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git submodule add https://github.com/google/googletest third-party/gtest
Клонирование в «/home/marialuneva/marlinez/workspace/projects/lab05/third-party/gtest»...
remote: Enumerating objects: 27977, done.
remote: Counting objects: 100% (230/230), done.
remote: Compressing objects: 100% (143/143), done.
remote: Total 27977 (delta 148), reused 88 (delta 87), pack-reused 27747 (from 2)
Получение объектов: 100% (27977/27977), 13.47 МиБ | 1.59 МиБ/с, готово.
Определение изменений: 100% (20737/20737), готово.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cd third-party/gtest && git checkout release-1.8.1 && cd ../..
Примечание: переключение на «release-1.8.1».

marialuneva@1511:~/marlinez/workspace/projects/lab05$ git rebase --continue 
Успешно перемещён и обновлён refs/heads/master.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
Текущая ветка master уже в актуальном состоянии.
Вы сейчас в состоянии «отсоединённого указателя HEAD». Можете осмотреться,
внести экспериментальные изменения и зафиксировать их, также можете
отменить любые коммиты, созданные в этом состоянии, не затрагивая другие
ветки, переключившись обратно на любую ветку.

Если хотите создать новую ветку для сохранения созданных коммитов, можете
сделать это (сейчас или позже), используя команду switch с параметром -c.
Например:

  git switch -c <новая-ветка>

Или отмените эту операцию с помощью:

  git switch -

Отключите этот совет, установив переменную конфигурации
advice.detachedHead в значение false

HEAD сейчас на 2fe3bd99 Merge pull request #1433 from dsacre/fix-clang-warnings
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add third-party/gtest
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git commit -m"added gtest framework"
[master 9510a5d] added gtest framework
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 third-party/gtest
marialuneva@1511:~/marlinez/workspace/projects/lab05$ gsed -i '/option(BUILD_EXAMPLES "Build examples" OFF)/a\
> option(BUILD_TESTS "Build tests" OFF)
' CMakeLists.txt
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cat >> CMakeLists.txt <<EOF
> if(BUILD_TESTS)
  enable_testing()
  add_subdirectory(third-party/gtest)
  file(GLOB \${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
  add_executable(check \${\${PROJECT_NAME}_TEST_SOURCES})
  target_link_libraries(check \${PROJECT_NAME} gtest_main)
  add_test(NAME check COMMAND check)
endif()
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab05$ mkdir tests
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cat > tests/test1.cpp <<EOF
> #include <print.hpp>

#include <gtest/gtest.h>

TEST(Print, InFileStream)
{
  std::string filepath = "file.txt";
  std::string text = "hello";
  std::ofstream out{filepath};

  print(text, out);
  out.close();

  std::string result;
  std::ifstream in{filepath};
  in >> result;

  EXPECT_EQ(result, text);
}
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cmake -H. -B_build -DBUILD_TESTS=ON
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
CMake Deprecation Warning at third-party/gtest/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at third-party/gtest/googlemock/CMakeLists.txt:42 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at third-party/gtest/googletest/CMakeLists.txt:49 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Warning (dev) at third-party/gtest/googletest/cmake/internal_utils.cmake:239 (find_package):
  Policy CMP0148 is not set: The FindPythonInterp and FindPythonLibs modules
  are removed.  Run "cmake --help-policy CMP0148" for policy details.  Use
  the cmake_policy command to set the policy and suppress this warning.

Call Stack (most recent call first):
  third-party/gtest/googletest/CMakeLists.txt:84 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Found PythonInterp: /usr/bin/python3 (found version "3.12.3") 
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (0.6s)
-- Generating done (0.0s)
-- Build files have been written to: /home/marialuneva/marlinez/workspace/projects/lab05/_build
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cmake --build _build
[  8%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 16%] Linking CXX static library libprint.a
[ 16%] Built target print
[ 25%] Building CXX object third-party/gtest/googlemock/gtest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 33%] Linking CXX static library libgtest.a
[ 33%] Built target gtest
[ 41%] Building CXX object third-party/gtest/googlemock/gtest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Linking CXX static library libgtest_main.a
[ 50%] Built target gtest_main
[ 58%] Building CXX object CMakeFiles/check.dir/tests/test1.cpp.o
[ 66%] Linking CXX executable check
[ 66%] Built target check
[ 75%] Building CXX object third-party/gtest/googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 83%] Linking CXX static library libgmock.a
[ 83%] Built target gmock
[ 91%] Building CXX object third-party/gtest/googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library libgmock_main.a
[100%] Built target gmock_main
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cmake --build _build --target test
Running tests...
Test project /home/marialuneva/marlinez/workspace/projects/lab05/_build
    Start 1: check
1/1 Test #1: check ............................   Passed    0.00 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.01 sec
marialuneva@1511:~/marlinez/workspace/projects/lab05$ _build/check
Running main() from /home/marialuneva/marlinez/workspace/projects/lab05/third-party/gtest/googletest/src/gtest_main.cc
[==========] Running 1 test from 1 test case.
[----------] Global test environment set-up.
[----------] 1 test from Print
[ RUN      ] Print.InFileStream
[       OK ] Print.InFileStream (0 ms)
[----------] 1 test from Print (0 ms total)

[----------] Global test environment tear-down
[==========] 1 test from 1 test case ran. (0 ms total)
[  PASSED  ] 1 test.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ cmake --build _build --target test -- ARGS=--verbose
Running tests...
UpdateCTestConfiguration  from :/home/marialuneva/marlinez/workspace/projects/lab05/_build/DartConfiguration.tcl
UpdateCTestConfiguration  from :/home/marialuneva/marlinez/workspace/projects/lab05/_build/DartConfiguration.tcl
Test project /home/marialuneva/marlinez/workspace/projects/lab05/_build
Constructing a list of tests
Done constructing a list of tests
Updating test list for fixtures
Added 0 tests to meet fixture requirements
Checking test dependency graph...
Checking test dependency graph end
test 1
    Start 1: check

1: Test command: /home/marialuneva/marlinez/workspace/projects/lab05/_build/check
1: Working Directory: /home/marialuneva/marlinez/workspace/projects/lab05/_build
1: Test timeout computed to be: 10000000
1: Running main() from /home/marialuneva/marlinez/workspace/projects/lab05/third-party/gtest/googletest/src/gtest_main.cc
1: [==========] Running 1 test from 1 test case.
1: [----------] Global test environment set-up.
1: [----------] 1 test from Print
1: [ RUN      ] Print.InFileStream
1: [       OK ] Print.InFileStream (0 ms)
1: [----------] 1 test from Print (0 ms total)
1: 
1: [----------] Global test environment tear-down
1: [==========] 1 test from 1 test case ran. (0 ms total)
1: [  PASSED  ] 1 test.
1/1 Test #1: check ............................   Passed    0.00 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.00 sec
marialuneva@1511:~/marlinez/workspace/projects/lab05$ gsed -i 's/lab04/lab05/g' README.md
marialuneva@1511:~/marlinez/workspace/projects/lab05$ gsed -i 's/\(DCMAKE_INSTALL_PREFIX=_install\)/\1 -DBUILD_TESTS=ON/' .travis.yml
marialuneva@1511:~/marlinez/workspace/projects/lab05$ gsed -i '/cmake --build _build --target install/a\
> - cmake --build _build --target test -- ARGS=--verbose
> ' .travis.yml
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add .travis.yml
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add tests
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add -p
diff --git a/CMakeLists.txt b/CMakeLists.txt
index 96a361e..89739e7 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -4,6 +4,7 @@ set(CMAKE_CXX_STANDARD 11)
 set(CMAKE_CXX_STANDARD_REQUIRED ON)
 
 option(BUILD_EXAMPLES "Build examples" OFF)
+option(BUILD_TESTS "Build tests" OFF)
 
 project(print)
 
(1/2) Индексировать этот блок [y,n,q,a,d,j,J,g,/,e,?]? q

marialuneva@1511:~/marlinez/workspace/projects/lab05$ git commit -m"added tests"
[master 06c46d5] added tests
 2 files changed, 21 insertions(+), 1 deletion(-)
 create mode 100644 tests/test1.cpp
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
Уже актуально.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git push origin master
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 35, готово.
Подсчет объектов: 100% (35/35), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (13/13), готово.
Запись объектов: 100% (15/15), 4.01 КиБ | 4.01 МиБ/с, готово.
Всего 15 (изменений 2), повторно использовано 8 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/marlinez/lab05
   ae69e0f..5a01e80  master -> master
# lab05
Сжатие объектов: 100% (25/25), готово.
Запись объектов: 100% (33/33), 9.05 КиБ | 4.52 МиБ/с, готово.
Всего 33 (изменений 8), повторно использовано 18 (изменений 3), повторно использовано пакетов 0
remote: Resolving deltas: 100% (8/8), done.
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
remote:        https://github.com/marlinez/lab05/security/secret-scanning/unblock-secret/2v5QLJglutUuYpDTgOxrYKBNISi
remote:     
remote: 
remote: 
To https://github.com/marlinez/lab05
 ! [remote rejected] master -> master (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «https://github.com/marlinez/lab05»
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git push origin master
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 35, готово.
Подсчет объектов: 100% (35/35), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (25/25), готово.
Запись объектов: 100% (33/33), 9.05 КиБ | 2.26 МиБ/с, готово.
Всего 33 (изменений 8), повторно использовано 18 (изменений 3), повторно использовано пакетов 0
remote: Resolving deltas: 100% (8/8), done.
To https://github.com/marlinez/lab05
   a21f244..06c46d5  master -> master
marialuneva@1511:~/marlinez/workspace/projects/lab05$ 

