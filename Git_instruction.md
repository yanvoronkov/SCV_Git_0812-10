![logo](git.svg)
# Работа c GIT
## 1. Проверка наличия установленного GIT
В терминале выполнить команду `git version`

Если GIT установлен, появится сообщение с информацией о версии программы. Иначе будет сообщение об ошибке.

## 2. Установка GIT
Загружаем последнюю версию **GIT** с сайта https://git-scm.com/downloads. Устанавлиаем с настройками по умолчанию.

## 3. Настройка GIT
При первом использовании GIT необходимо представиться. Для этого в терминале нужно выполнить две команды:
```
git config --global user.name «Ваше имя английскими буквами»
git config --global user.email ваша почта@example.com
```

## 4. Инициализация репозитория
Если у вас уже есть проект в каталоге git_manual, который не находится под версионным контролем Git, то для начала нужно перейти в него. Для этого открыть терминал и перейти в рабочую папку (пример команды):
```
$ cd /Users/yan/Desktop/web_developer/GeekBrains/git_education/git_manual
````
Эта команда создаёт в текущем каталоге новый подкаталог с именем .git, содержащий все необходимые файлы репозитория — структуру Git репозитория.
Получить репозиторий можно двумя способами.
1. В терминале переходим к папке в которой хотим создать репозиторий и выполняем команду:
```
git init
```
2. Клонировать существующий репозиторий git из любого места. Сделать это можно так:
```
git clone <адрес репозитория>
```

## 5. Запись изменений в репозиторий
Для проверки статуса изменений выполнить команду 
```
$ git status
```
Для добавления под версионный контроль существующего в каталоге файла, нужно добавить его в индекс командой
```
$ git add
```
указав индексируемые файлы и осуществить первый коммит изменений командой
```
$ git commit -m
```
записав соотвествующий комментарий сделанных изменений.
Для просмотра сделанных изменений в файле выполним команду
```
$ git diff
```

## 6. Просмотр истории коммитов
Чтобы просмотреть историю коммитов, нужно выполнить команду
```
$ git log
```
Для вывода истории коммитов в кратком виде используйте команду
```
$ git reflog
```

## 7. Перемещение между сохранениями
Для перемещения между сохранениями необходимо ввести команду
```
$ git checkout
```
и первые 4 символа хэш-номера коммита.

## 8. Игнорирование файлов
Для того, чтобы исключить из отслеживания в репозитории файлы и папки, необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответствующие таким файлам и/или папкам, например _*.jpeg._
![logo](gitignore.png)

Также можно проигнорировать целую папку, указав ее название в файле .gitignore, например ***/temp***

## 9. Создание веток git
Ветка в Git - это простой перемещаемый указатель на один из коммитов, обычно последний в цепочке коммитов.
По умолчанию имя основной ветки в Git - master.

Для создания новой ветки используется команда 
```
git branch <branch name>
```
где ***branch name*** - имя создаваемой ветки.

После создания ветки нужно переместиться в указанную ветку командой:
```
git checkout <branch name>
```
Далее мы можем работать в новой созданной ветке и сохранять и коммитить внесенные изменения. После согласования и проверки всех изменений, можно сделать сляние текущей ветки с основной веткой проекта.

## 10. Сляние веток и разрешение конфликтов
Для слияния рабочей ветки с основной веткой проекта нужно использовать команду 
```
git merge <branch name>
```
где ***branch name*** - имя ветки, которую мы сливаем с текущей веткой, в которой находимся. При слиянии веток, когда в файле главной ветки и том же файле сливаемой ветки происходти конфликт версий. В этом случае, git предоставляет возможность вручную пользователю выбрать нужную версию файла. 

После выбора нужной версии и редактирования файла, нужно произвести сохранение и коммит.

## 11. Удаление веток
После слияния веток, если черновая ветка нам больше не нужна, мы можем ее удалить, воспользовавшись командой:
```
git branch -d <branch name>
```
где ***branch name*** - имя удаляемой ветки. Если слияние не сделано, то данной командой ветка удалена не будет и Git выдаст уведомление о том, что слияние с главной веткой не выполнено. 

Если слияние делать не нужно, а нужно просто удалить ветку, тогда нужно использовать команду:
```
git branch -D <branch name>
```
После выполнения этой команды ветка ***branch name*** будет удалена.
## 12. Работа с удаленными репозиториями

Удаленный репозиторий используется для командной работы над проектами. Находится на внешнем ресурсе. Одним из самых популярных ресурсов для удаленных репозиториев является ресур GitHub. 

Для начала работы необходимо зарегистрироваться на GitHub.

Разместить репозиторий на GitHub можно несколькими методами.
1. Создать репозиторий на GitHub. Затем создать репозиторий на локальном компьютере, инициализировать его. 
Далее переименовать ветку локального депозитория, если она называется не main, так как в GitHub главная ветка называется main. Для этого используем команду:
```
git branch -M main
```
Далее связываем локальный депозиторий с удаленным на GitHub командой:
```
git remote add origin <url удаленного репозитория>
```
2. Создать новый репозиторий на GitHub и затем склонировать его командой
```
git clone <url репозитория на GitHub>
```
После сделаных изменений в локальном репозитории можно отправить данные на удаленный репозиторий. Для этого нужно выполнить команду: 
```
git push -u origin main
```
Для обновления файлов локального депозитория файлами с удаленного репозитория, используется команда:
```
git pull
```
Также можно сделать ответвление общедоступного репозитория в свой аккаунт GitHub командой командой ***fork*** на GitHub. Затем можно сделать свои изменения и доработки в файлах изатем отправить эти изменения командой ***Pull request*** автору репозитория.