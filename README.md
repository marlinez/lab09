# lab04
marialuneva@1511:~$ export GITHUB_USERNAME=marlinez
marialuneva@1511:~$ export GITHUB_EMAIL=export GITHUB_EMAIL=maria15lun@mail.ru
marialuneva@1511:~$ export GITHUB_TOKEN=<token>
marialuneva@1511:~$ alias edit=nano
marialuneva@1511:~$ cd ${GITHUB_USERNAME}/workspace
marialuneva@1511:~/marlinez/workspace$ source scripts/activate
marialuneva@1511:~/marlinez/workspace$ cat > ~/.config/hub <<EOF
> github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF
marialuneva@1511:~/marlinez/workspace$ git config --global hub.protocol https
marialuneva@1511:~/marlinez/workspace$ mkdir projects/lab02 && cd projects/lab02
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git init
подсказка: Using 'master' as the name for the initial branch. This default branch name
подсказка: is subject to change. To configure the initial branch name to use in all
подсказка: of your new repositories, which will suppress this warning, call:
подсказка: 
подсказка: 	git config --global init.defaultBranch <name>
подсказка: 
подсказка: Names commonly chosen instead of 'master' are 'main', 'trunk' and
подсказка: 'development'. The just-created branch can be renamed via this command:
подсказка: 
подсказка: 	git branch -m <name>
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git config --global user.name ${GITHUB_USERNAME}
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git config --global user.email ${GITHUB_EMAIL}
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git config -e --global
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git pull origin master
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (3/3), 1.44 КиБ | 1.44 МиБ/с, готово.
Из https://github.com/marlinez/lab02
 * branch            master     -> FETCH_HEAD
 * [новая ветка]     master     -> origin/master
marialuneva@1511:~/marlinez/workspace/projects/lab02$ touch README.md
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	README.md

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git add README.md
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git commit -m"added README.md"
[master 28e8a7a] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git push origin master
Username for 'https://github.com': marlinez
Password for 'https://marlinez@github.com': 
Перечисление объектов: 4, готово.
Подсчет объектов: 100% (4/4), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 277 байтов | 277.00 КиБ/с, готово.
Всего 3 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: This repository moved. Please use the new location:
remote:   https://github.com/marlinez/Lab02.git
To https://github.com/marlinez/lab02.git
   e05f658..28e8a7a  master -> master
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (3/3), 980 байтов | 980.00 КиБ/с, готово.
Из https://github.com/marlinez/lab02
 * branch            master     -> FETCH_HEAD
   28e8a7a..e05e466  master     -> origin/master
Обновление 28e8a7a..e05e466
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git log
commit e05e46604220eb153522e69cb21ef271771dbb87 (HEAD -> master, origin/master)
Author: marlinez <maria15lun@mail.ru>
Date:   Sun Mar 2 19:28:50 2025 +0300

    Create .gitignore

commit 28e8a7ae652e231dd4467ae646edc79c2be7d4b4
Author: marlinez <maria15lun@mail.ru>
Date:   Sun Mar 2 19:23:23 2025 +0300

    added README.md

commit e05f65811fe99c3cfec00c8e6a1267650c8ed3fa
Author: marlinez <maria15lun@mail.ru>
Date:   Sun Mar 2 19:12:38 2025 +0300

    Initial commit
marialuneva@1511:~/marlinez/workspace/projects/lab02$ mkdir sources
marialuneva@1511:~/marlinez/workspace/projects/lab02$ mkdir include
marialuneva@1511:~/marlinez/workspace/projects/lab02$ mkdir examples
marialuneva@1511:~/marlinez/workspace/projects/lab02$ cat > sources/print.cpp <<EOF
> #include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab02$ cat > include/print.hpp <<EOF
> #include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab02$ cat > examples/example1.cpp <<EOF
> #include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab02$ cat > examples/example2.cpp <<EOF
> #include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
marialuneva@1511:~/marlinez/workspace/projects/lab02$ edit README.md
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	examples/
	include/
	sources/

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git add .
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git commit -m"added sources"
[master eaf240d] added sources
 4 files changed, 32 insertions(+)
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
marialuneva@1511:~/marlinez/workspace/projects/lab02$ git push origin master
Username for 'https://github.com': marlinez 
Password for 'https://marlinez@github.com': 
Перечисление объектов: 10, готово.
Подсчет объектов: 100% (10/10), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (7/7), готово.
Запись объектов: 100% (9/9), 959 байтов | 959.00 КиБ/с, готово.
Всего 9 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: This repository moved. Please use the new location:
remote:   https://github.com/marlinez/Lab02.git
To https://github.com/marlinez/lab02.git
   e05e466..eaf240d  master -> master
marialuneva@1511:~/marlinez/workspace/projects/lab02$ 
>>>>>>> 8ea0a69 (Add files via upload)
