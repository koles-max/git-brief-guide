# Git

**Git** -- это система контроля версий:  

- позволяет хранить историю изменений
- помогает синхронизировать изменения, сделанные разными участниками команды
- позволяет хранить несколько версий проекта
- изменения хранятся в коммитах
- идентификатором коммита выступает его SHA-1 хеш
- последовательности коммитов образуют ветки
- может существовать несколько веток
- основная ветка называется master или main
- ветки могут объединяться
- вся служебная информация хранится в папке .git
- файл HEAD хранит ссылку на служебный файл в котором записан хеш последнего коммита
  
[Официальная страница загрузки](https://git-scm.com/download/)

---

**Git** имеет интерфейс командной строки, для работы с которым полезно знать основные команды для работы с файлами:  
- ```pwd``` - вывести текущий каталог
- ```ls -a <dir>``` - вывести список всех папок и файлов в каталоге _dir_
- ```cd <dir>``` - сменить текущий каталог на _dir_
- ```~``` - домашний, ```.``` - текущий, ```..``` - родительский, ```/``` - корневой каталоги
- ```mkdir <dir1> <dir2> ...``` - создать каталоги _dir1, dir2, ..._
- ```mkdir -p <dir>``` - создать каталог _dir_ и весь путь до него (если уже есть, ошибки не возникнет)
- ```touch <file1> <file2> ...``` - создать файлы _file1, file2, ..._
- ```rm <file1> <file2> ...``` - удалить файлы _file1, file2, ..._
- ```rmdir <dir1> <dir2> ...``` - удалить пустые каталоги _dir1, dir2, ..._
- ```rm -r <dir1> <dir2> ...``` - удалить рекурсивно каталоги _dir1, dir2, ..._
- ```cp <file1> <file2> ... <dir>``` - копировать файлы _file1, file2, ..._ в каталог _dir_
- ```mv <file1> <file2> ... <dir>``` - переместить файлы _file1, file2, ..._ в каталог _dir_
- ```cat <file1> <file2> ...``` - сконкатенировать и вывести содержимое файлов _file1, file2, ..._
- ```&&``` - для выполнения нескольких команд сразу
- Стрелки вверх и вниз - перемещение по историии команд
- Tab - дополнение названий команд и файлов папок по первым символам
- ```HEAD``` - синоним хеша последнего коммита

---

## Команды для работы с Git

- ```git version``` - проверка версии Git
- ```git config --global user.name "John Smith"``` - задать имя пользователя в глобальных настройках Git
- ```git config --global user.email "john@server.com"``` - задать e-mail пользователя в глобальных настройках Git
- ```git config user.name "John Smith"``` - задать имя пользователя в настройках репозитория в рабочем каталоге
- ```git config user.email "john@server.com"``` - задать e-mail пользователя в настройках репозитория в рабочем каталоге
- ```cat ~/.gitconfig``` - вывести содержимое файла с глобальными настройками Git
- ```git config --list``` - вывести настройки git (результат зависит от текущего каталога, к глобальным настройкам git добавляются настройки репозитория из текущего каталога)
- ```git init``` - сделать рабочий каталог репозиторием (внутри рабочего каталога будет создан подкаталог .git в котором будет храниться вся служебная информация)
- ```rm -rf .git``` - "разгитить" рабочий каталог
- ```git status``` - проверить статус репозитроия
- ```git add <file1> <file2>``` - добавить файлы _file1, file2_ к подготавливаемому коммиту
- ```git add -all``` - добавить все изменения к подготавливаемому коммиту
- ```git add .``` - добавить всю текущую папку к подготавливаемому коммиту
- ```git commit -m "Комментарий к коммиту"``` - сделать коммит подготовленных (staged) изменений с сопутствующим комментарием
- ```git log``` - просмотреть историю коммитов
- ```git log --oneline``` - просмотреть список коммитов в формает сокр. хеш + комментарий к коммиту
- ```git remote add origin git@github.com:%ИМЯ_АККАУНТА%/%НАЗВАНИЕ ПРОЕКТА%.git``` - привязать к локальному удалённый репозиторий с указанным URL под именем origin
- ```git remote -v``` - убедиться, что локальный репозиторий связан с удалённым
- ```git push -u origin main``` - первая отправка изменений на удалённый репозиторий
- ```git push``` - последующие

---

# GitHub

[**GitHub**](https://github.com) - самый популярный сервис для размещения удалённых репозиториев  
Для удобства работы с удалённым репозиторием можно использовать SSH.  
Создать пару публичный/приватный ключ можно командой  
```
$ cd ~ # перешли в домашнюю директорию
$ ls -la .ssh/ # вывели список созданных ключей, если ничего нет
$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" # создаём пару ключей
$ ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" # или так
```
после чего содердимое ```pub-файла``` надо загрузить в _GitHub->Settings->SSH and GPG keys->New SSH key_  
Проверить работоспособность SSH можно командой ```$ ssh -T git@github.com```

---

## README.md

Файл ```README.md``` в корне репозитория предназначен для описания проекта и использует язык разметки **markdown**  
[Гайд по markdown](https://www.markdownguide.org/cheat-sheet/)  
[Шпаргалка на GitHub](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c)

# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6

text<br>above<br>line

---

text  
below  
line

12345
67890

*italic* _text_  
**bold** __text__  
~~strikeout text~~

1. numerated
2. list

* unordered
* list

---

- one more
- unordered list

[Yandex link](https://www.yandex.ru "I'm Yandex!")

```bash
cd ~
ls -la
```

```html
<h1>HTML Header 1</h1>
```

![Image Alt Text](/images/sample.webp "Nice Sample Image")
