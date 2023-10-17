# Шпаргалка по git-у

## Синхронизация локального и удалённого репозиториев
* `git remote add origin https://github.com/YandexPracticum/first-project.git` (от англ. remote, «удалённый» + add, «добавить») — привяжи локальный репозиторий к удалённому с URL https://github.com/YandexPracticum/first-project.git;<br>
* `git remote -v` (от англ. verbose, «подробный») — проверь, что репозитории действительно связались;<br>
* `git push -u origin main` (от англ. push, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием origin.<br>
* `git push` (от англ. push, «толкать») — загрузи коммиты в удалённый репозиторий после того, как он был привязан с помощью флага -u.

## **Навигация**

* `$ pwd` (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;<br>
* `$ ls` (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;<br>
* `$ ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа .;<br>
* `$ cd first-project` (от англ. change directory, «сменить директорию») — перейди в папку first-project;<br>
* `$ cd first-project/html` — перейди в папку html, которая находится в папке first-project;<br>
* `$ cd ..` — перейди на уровень выше, в родительскую папку;<br>
* `$ cd ~` — перейди в домашнюю директорию (/Users/Username);<br>
* `$ cd /` — перейди в корневую директорию.<br>

## **Работа с файлами и папками**

`$ touch index.html` (англ. touch, «коснуться») — создай файл index.html в текущей папке;<br>
`$ touch index.html style.css script.js` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;<br>
`$ mkdir second-project` (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.<br>

## **Копирование и перемещение**
`$ cp file.txt ~/my-dir` (от англ. copy, «копировать») — скопируй файл в другое место;<br>
`$ mv file.txt ~/my-dir` (от англ. move, «переместить») — перемести файл или папку в другое место.<br>


## **Чтение**
`$ cat file.txt` (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.<br>


## **Удаление**
`$ rm about.html` (от англ. remove, «удалить») — удали файл about.html;<br>
`$ rmdir images` (от англ. remove directory, «удалить директорию») — удали папку images;<br>
`$ rm -r second-project` (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.<br>


## **КОММИТ**

`$ git init` # Инициализировать репозиторий<br>
`$ git status` # Проверить статус, или состояние репозитория.<br>
`$ rm -rf .git` # удалить подпапку .git, "разгитить" папку — удалить скрытую подпапку .git ($ cd <папка с репозиторием> # сначала перейти в папку)<br>
`$ git commit -m` ‘Мой первый коммит!’ # закоммитить проект с месседжом<br>
`$ git log` # Просмотреть историю коммитов<br>
`$ git log --oneline` #Сокращенный лог


## **Добавить файлы к отслеживанию**

`$ git add todo.txt` # подготовить к сохранению 1 файл todo.txt<br>
`$ git add --all` # подготовили к сохранению все файлы в репозитории<br>
`$ git add .` # добавить всю текущую папку<br>
`$ git status` - отследить состояние репозитория <br>

## *Что такое Хеш*

Хеш — основной идентификатор коммита. Хеш можно будет передавать в качестве параметра разным Git-командам, чтобы указать, с каким коммитом нужно произвести то или иное действие.
Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке .git в репозитории проекта.<br>


*Таким образом:*<br>
* Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.<br>
* Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.<br>
* Все хеши, а также таблицу соответствий хеш → информация о коммите Git хранит в папке .git.<br>

## *Что такое (HEAD -> master\main)*

Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).<br>
Вместо хеша последнего коммита можно написать слово HEAD — Git вас поймёт.<br>

## Статусы файлов в Git

Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом.


**Основные статусы:**
* `untracked` - неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду git add.<br>
* `staged` (indexed, cached) - подготовленные файлы. Описывает список файлов, которые войдут в коммит.<br> 
* `tracked` -  файлы, которые уже были зафиксированы с помощью git commit, а также файлы, которые были добавлены в staging area командой git add. То есть все файлы, в которых Git так или иначе отслеживает изменения.<br>
* `modified` - Состояние modified означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.<br>


*Про staged и modified*
Команда git add добавляет в staging area только текущее содержимое файла. Если вы, например, сделаете git add file.txt, а затем измените file.txt, то новое содержимое файла не будет находиться в staging.<br>
Git сообщит об этом с помощью статуса modified: файл изменён относительно той версии, которая уже в staging. Чтобы добавить в staging последнюю версию, нужно выполнить git add file.txt ещё раз.<br>

## Дополнение\изменение последнего коммита


* Флаг `--amend` рассчитан на работу с последним коммитом (HEAD).<br>
* Дополнить коммит новыми файлами можно с помощью `git commit --amend --no-edit`. Благодаря опции `--no-edit` сообщение к коммиту останется таким, каким и было.<br>
* Изменить сообщение к коммиту позволяет команда `git commit --amend -m "Обновлённое сообщение коммита"`.<br>

## Откат

* Команда `git restore --staged <file>` переведёт **уже закоммиченный** файл из staged обратно в modified или untracked.<br>
* Команда `git reset --hard <commit hash>` «откатит» историю до коммита с указанным хешем <hash>. Более поздние коммиты потеряются!<br>
* Команда `git restore <file>` «откатит» изменения **в файле** до последней сохранённой (в коммите или в staging) версии.<br>

## Изменения в файлах

* `git diff` - позволяет отслеживать изменения в еще незакоммиченных файлах по отношению к уже закоммиченным т.е. (сравнит последнюю закоммиченную версию файла с текущей (изменённой) версией.) По умолчанию команда git diff не показывает изменения в staged-файлах — только в modified. Чтобы всё-таки просмотреть изменения в staged (подготовленных к коммиту), нужно использовать флаг --staged: `git diff --staged`.<br> 

### Особенности вывода команды git diff:

* Красная строка (-) - удаленные строки<br>
* Зеленая строка (+) - добавленные строки<br>
* `diff --git a/... b/...` и `index 901da07..ac459e1 100644` - низкоуровневая техническая информация<br>
* Строки `--- a/teremok.txt` и +++ `b/teremok.txt` сообщают о выведении результата сравнения файлов `a/teremok.txt` и `b/teremok.txt` - исходной и текущей версии файлов.<br>
* Строка @@ -1,2 +1,2 @@ сообщает, какие строки файла попали в сравнение. Выражение 1,2 (неважно, с плюсом или с минусом) говорит, что были использованы две строки, начиная с первой. Если бы было, например, написано +15,7, это значило бы, что в сравнении участвуют 7 строк, начиная с 15-й.<br>
* Выражение со знаком минус (-1,2) относится к «оригинальной» версии файла `(a/teremok.txt)`, а со знаком плюс (+1,2) — к «изменённой» `(b/teremok.txt)`.<br>

### Сопостовление коммитов

* `git diff <hash1> <hash2>` - команда, позволяющая сопоставить содержимое двух коммитов. Состояние файлов на момент первого переданного коммита будет сравниваться с состоянием файлов на момент второго. Вместо <hash2> можно использовать HEAD: git diff <hash1> HEAD, потому что HEAD указывает на последний коммит.<br>

**Порядок аргументов**: По сути команда `git diff A B` выводит список инструкций: как превратить состояние A в состояние B. Если поменять A и B местами `git diff B A`, то и инструкции будут обратные: как превратить B в A. При этом все зелёные строки станут красными, и наоборот.<br>

Дописать строку в файл можно с использованием команды `echo`. Сама по себе эта команда просто выводит в консоль то, что ей передали в качестве параметра. Но если скомбинировать `echo` с символами перенаправления вывода `>>` (два знака «больше»), то всё, что должно было попасть на экран, вместо этого будет записано в файл.<br>

* Оператор `>>` — это возможность командной строки (Bash). Его можно использовать не только с `echo`, но и с любой другой командой, которая выводит что-то на экран.
Одинарный символ `>` тоже перенаправит вывод команды в файл, но перед этим **сотрёт содержимое файла**, то есть перезапишет файл целиком.

## Игнорирование файлов в Git

Часто бывает так, что в папке-репозитории есть файлы, для которых не нужно хранить историю изменений. Чтобы Git игнорировал такие файлы и не пытался добавить их в репозиторий, нужно создать файл `.gitignore` (от англ. ignore — «игнорировать») и записать в него названия игнорируемых файлов. С точки зрения Git `.gitignore` — это обычный текстовый файл. Его добавляют в корень репозитория и тоже коммитят. В простейшем случае в `.gitignore` указывают все файлы, которые нужно игнорировать (по одному имени на строку). Но часто удобнее использовать **шаблоны**. Необходимые шаблоны для задания игнорируемых файлов и папок можно найти в Интернете. <br> 

## Клонирование
Процесс копирования удалённого репозитория на локальный компьютер называется **клонированием**. Клонирование репозитория — обычно первое, что делает разработчик на новом месте работы.<br>

`git clone` (от англ. clone — «клон», «копия») - создаст копию удалённого репозитория на вашем компьютере. В качестве параметра команде нужно передать адрес репозитория, который вы скопировали на GitHub.<br>

Команда `git clone` автоматически связывает локальный и удалённый репозиторий. То есть если в GitHub-репозитории что-то поменяется (например, добавятся коммиты), вам не нужно будет заново клонировать его. Достаточно будет выполнить команду, которая обновит вашу копию.<br>


## Fork
Fork (англ. «развилка», «ответвление»), или «форк», — это GitHub-операция; напрямую с Git она не связана. «Форк» создаёт копию репозитория в аккаунте GitHub. Такая копия будет полностью независима. Изменения, которые вы внесёте, не будут синхронизированы с исходным репозиторием.<br>
В процессе «форка» создаётся копия всех файлов, истории коммитов и веток. Эта копия сохраняется в вашей учётной записи GitHub.<br>

## Ветки или BRANCHES

Ветка (англ. branch) — это изолированный поток разработки проекта. В таком потоке можно проверять разные идеи, тестировать новую функциональность и так далее.<br>

Благодаря веткам несколько человек могут работать над одним репозиторием и не мешать друг другу. А ещё ветки помогают декомпозировать большую и страшную задачу на маленькие и понятные.<br>
Основная версия проекта хранится в главной ветке main (или master).<br>
С помощью команды `git branch` можно посмотреть, какие в проекте есть ветки и в какой из них вы сейчас находитесь.<br>

### Создание ветки

Для создания веток в Git есть команда `git branch` с параметром в виде названия ветки: `git branch <название_ветки>`. Например, создадим ветку с названием `feature/add-branch-info`.<br>

Название ветки в Git может состоять из букв, цифр, а также включать любой из четырёх символов: `.`, `-`, `_`, `/`. Эти символы не несут особого смысла. Например, ветка `feature/add-branch-info` могла бы называться `feature_add-branch-info` или `feature-add-branch`. Обратите внимание, что ветки не образуют иерархии, как директории, разделённые символом `/`.<br>

### Переход с ветки на ветку



