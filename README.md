marialuneva@1511:~$ export GITHUB_USERNAME=marlinez
marialuneva@1511:~$ export GITHUB_TOKEN=<token>
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
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (4/4), 1.48 КиБ | 1.48 МиБ/с, готово.
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
 * [новая ветка]     master     -> origin/master
dropping d8450f9b0cac6ae76101016a5db43ca582b74618 Initial commit -- patch contents already upstream
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
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
fatal: It seems that there is already a rebase-merge directory, and
I wonder if you are in the middle of another rebase.  If that is the
case, please try
	git rebase (--continue | --abort | --skip)
If that is not the case, please
	rm -fr ".git/rebase-merge"
and run me again.  I am stopping in case you still have something
valuable there.

marialuneva@1511:~/marlinez/workspace/projects/lab05$ git rebase --continue 
Успешно перемещён и обновлён refs/heads/master.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git pull origin master
Из https://github.com/marlinez/lab05
 * branch            master     -> FETCH_HEAD
Текущая ветка master уже в актуальном состоянии.
marialuneva@1511:~/marlinez/workspace/projects/lab05$ git push origin master
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 17, готово.
Подсчет объектов: 100% (17/17), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (13/13), готово.
Запись объектов: 100% (15/15), 4.01 КиБ | 4.01 МиБ/с, готово.
Всего 15 (изменений 2), повторно использовано 8 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/marlinez/lab05
   ae69e0f..5a01e80  master -> master
# lab05
