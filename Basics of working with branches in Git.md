# Клонируем репозиторий


## Клонировать репозиторий — git clone


[Клонировать](https://pictures.s3.yandex.net/resources/M3_T2_01_1687524779.png)

Теперь откройте консоль, перейдите в папку, в которую хотите положить репозиторий, и выполните команду git clone (от англ. clone — «клон», «копия»). 

Она создаст копию удалённого репозитория на вашем компьютере. 

В качестве параметра команде нужно передать адрес репозитория, который вы только что скопировали на GitHub.


```
$ git clone https://github.com/yandex-praktikum/git-clone-lesson # укажите адрес репозитория, который нужно склонировать

```

Команда git clone автоматически связывает локальный и удалённый репозиторий. 

То есть если в GitHub-репозитории что-то поменяется (например, добавятся коммиты), вам не нужно будет заново клонировать его. 

Достаточно будет выполнить команду, которая обновит вашу копию.

Убедитесь в том, что репозитории связаны, командой git remote -v.

```
$ cd git-clone-lesson

$ git remote -v

origin    git@github.com:yandex-praktikum/git-clone-lesson.git (fetch)
origin    git@github.com:yandex-praktikum/git-clone-lesson.git (push)

```


# Выполняем Fork


## Что такое Fork


Fork (англ. «развилка», «ответвление»), или «форк», — это GitHub-операция; напрямую с Git она не связана. «Форк» создаёт копию репозитория в аккаунте GitHub.

Такая копия будет полностью независима. Изменения, которые вы внесёте, не будут синхронизированы с исходным репозиторием.

В процессе «форка» создаётся копия всех файлов, истории коммитов и веток. Эта копия сохраняется в вашей учётной записи GitHub.

Вот некоторые из распространённых причин использования «форков»:

* Вы хотите внести свой вклад в проект (например, open source), но не имеете прав на изменение исходного репозитория.
 
Тогда вы можете сделать «форк», добавить нужные правки, а затем отправить запрос на включение этих изменений в оригинальный проект.

* Вы хотите развивать проект независимо от исходного. 

Допустим, создатели проекта решили, что не будут добавлять функциональность, которая вам необходима. 

В таком случае вы можете сделать «форк» и добавить её самостоятельно.


## Применяем Fork

[перейди по ссылке](https://github.com/yandex-praktikum/git-basics)


[и нажмите на кнопку Fork в правом верхнем углу](https://pictures.s3.yandex.net/resources/M3_T2_01-2_1687525544.png)

В открывшемся окне вы можете поменять название и описание репозитория.

Или поставить галку, чтобы склонировать только главную ветку вместо всех сразу.

Нажмите Create fork (англ. **«создать копию репозитория»).


[Create fork](https://pictures.s3.yandex.net/resources/M3_T2_02_1687525556.png)

Немного подождите, пока репозиторий скопируется. 

После этого он будет доступен по адресу https://github.com/%USERNAME%/git-basics, где %USERNAME% — ваше имя пользователя.

В результате вы получите полную копию исходного репозитория, которую можно свободно изменять и которой можно управлять.

💡 «Форк» или clone?

_Обычно комбинация «форк» + clone используется для внесения изменений в публичные репозитории._

_В этом случае «форк» становится подготовительным этапом перед клонированием чужого репозитория на ваш компьютер._

_Если репозиторий приватный или это репозиторий вашей компании, при работе с ним достаточно clone._



# Что такое ветка


## Зачем нужны ветки


### Просмотреть ветки проекта — git branch

Теперь покажем, как получить список веток проекта. Создайте тестовый проект learn_branches. 

Добавьте в него файл README.md, проиндексируйте изменения и сделайте коммит: git commit -m "Выполнить первый коммит". 

Вспомните, что несколько команд можно объединять в одной строке терминала символом логического «и» — &&.


```
$ mkdir learn_branches && cd learn_branches && git init # создали новый репозиторий

$ touch README.md # создали файл

$ git add . # команда git add с флагом-точкой подготовит к сохранению текущую папку; вместо этого можно вызвать git add --all

$ git commit -m "Выполнить первый коммит" 

```

Репозиторий создан, файлы добавлены и закоммичены. В репозитории появилась главная ветка. 

Это можно проверить командой для просмотра веток git branch.



```
$ git branch 

* main # мы в основной ветке

# чтобы выйти из просмотра веток, может понадобиться Q! 

```

При вызове git branch выводятся ветки, которые есть в проекте. Звёздочкой (*) отмечено, в какой ветке вы находитесь в текущий момент.

Сейчас проект learn_branches выглядит так.

[отображение ветки](https://pictures.s3.yandex.net/resources/M3_T3_02-4_1687851601.png)



### Дополняем ветку


Добавьте в README.md следующий текст.

```
# Описание

Это проект по изучению работы с ветками


$ git add . && git commit -m "Обновить README"

```

[отображение состояния ветки](https://pictures.s3.yandex.net/resources/M3_T3_01-2_1687851614.png)



# Создаём ветку


## Создать ветку — git branch <название_ветки>


Для создания веток в Git есть команда git branch с параметром в виде названия ветки: git branch <название_ветки>. 

Например, создадим ветку с названием feature/add-branch-info.

```
$ git branch feature/add-branch-info # создали ветку feature/add-branch-info

$ git branch # посмотрели ветки
  
  feature/add-branch-info  # появилась новая
* main                     # * значит, что мы находимся в основной ветке

```

Готово! Сейчас в вашем репозитории две ветки — основная и feature/add-branch-info.

[ветка feature](https://pictures.s3.yandex.net/resources/M3_T3_1687789327.png)



# Шагаем с ветки на ветку


## Переключиться на другую ветку — git checkout <название_ветки>


```
$ git checkout feature/add-branch-info # перешли в новую ветку

Switched to branch 'feature/add-branch-info'

$ git branch # проверили


* feature/add-branch-info # теперь находимся тут
  main

```

Строчка Switched to branch... (англ. «переключено на ветку…») сообщает, на какую ветку вы только что переключились.

Откройте файл README.md и добавьте в него информацию о командах git branch и git checkout. Получится следующее.


```
# Ветки в Git 

Чтобы создать ветку, необходимо выполнить команду `git branch %BRANCH_NAME%`.

Для перехода в ветку есть команда `git checkout %BRANCH_NAME%`.

```

Добавьте изменения в staging area и сделайте коммит с сообщением: ```git add . && git commit -m "Добавить git branch и git checkout в README"```. 

Сейчас история проекта выглядит так.

[результат команды](https://pictures.s3.yandex.net/resources/M3_T3_01-3_1687851879.png)



## Создать ветку и сразу переключиться на неё — git checkout -b <название_ветки>


Можно создать ветку и сразу начать в ней работать. За это отвечает команда ```git checkout с флагом -b``` (от англ. branch) и названием ветки. 

Эта команда делает то же самое, что и последовательность команд git branch %название-ветки% && git checkout %название-ветки%.

Убедитесь, что вы в основной ветке. Затем создайте ещё одну ветку для исправления ошибок bugfix/fix-branch и сразу переключитесь на неё.


```
$ git checkout main

$ git checkout -b bugfix/fix-branch # создали ветку и сразу на неё переключились

Switched to a new branch 'bugfix/fix-branch'

$ git branch


* bugfix/fix-branch # сразу в нужной ветке
  feature/add-branch-info
  main

```

Строчка Switched to a new branch... (англ. «переключено на новую ветку…») сообщает о том, что вы переключились на только что созданную ветку. 

Теперь история проекта выглядит так.


[результат команды](https://pictures.s3.yandex.net/resources/M3_T3_02-5_1687851910.png)


## На какой коммит указывает bugfix/fix-branch

Ветка в Git — это указатель на коммит. Когда вы делаете новый коммит в ветке, этот указатель передвигается вперёд.

Пока вы не вносили новые коммиты в ветку bugfix/fix-branch, поэтому она указывает на тот же коммит, что и основная ветка. 

Убедитесь в этом с помощью команды git log --oneline.


```
$ git checkout bugfix/fix-branch

$ git log --oneline

a7eb909 (HEAD -> bugfix/fix-branch, main) Добавить файл README


$ git checkout feature/add-branch-info

$ git log --oneline


abd591c (HEAD -> feature/add-branch-info) Добавить git branch и git checkout в README

a7eb909 (main, bugfix/fix-branch) Добавить файл README

```

Так что можно показать текущее состояние проекта git-branches так: поместить названия веток над коммитами, на которые они указывают.

[результат](https://pictures.s3.yandex.net/resources/M3_T3_02-6_1687851937.png)



**💡 Две ветки не могут указывать на один коммит: у каждой он должен быть свой?**

**_Могут: например, если в только что созданной ветке ещё не было новых коммитов._**



## Просматриваем все ветки: git branch -a


Команда git branch показывает только локальные ветки – те, которые существуют на вашем локальном компьютере. 

Например, вы склонировали себе репозиторий, в котором котором на сервере GitHub есть несколько веток.
 
В интерфейсе GitHub вы увидели, что есть ветка feature/add-branch-info и переключились на неё с помощью команды git checkout feature/add-branch-info.

Позже вы создали ветку bugfix/fix-branch с помощью команды git checkout -b bugfix/fix-branch.

Затем вернулись на ветку main: git checkout main. При вызове git branch вы увидите следующий вывод:


```
$ git branch

* main
  feature/add-branch-info
  bugfix/fix-branch

```

Когда вы работаете с несколькими ветками в проекте, полезно уметь просматривать все доступные ветки – хранящиеся как на вашем компьютере, так и на сервере GitHub.

Для этого используется команда git branch -a. Флаг -a в команде git branch -a означает “all” (англ. «все»). 

Использование этого флага позволяет команде отображать все ветки в репозитории:

* Локальные ветки будут указываться как обычно при вызове git branch, например, feature/add-branch-info.

* Удалённые – с префиксом remotes/origin: remotes/origin/feature/add-branch-info.

Отдельно будет указана основная ветка: строка с ней будет выглядеть как remotes/origin/HEAD -> origin/main. Прочитать эту строку можно как «Главной веткой является main».

Пример:


```
$ git branch -a


* main
  feature/add-branch-info
  bugfix/fix-branch
  remotes/origin/HEAD -> origin/main
  remotes/origin/feature/add-branch-info
  remotes/origin/main

```

В этом выводе вы видите список всех веток, где:

main, feature/add-branch-info, и bugfix/fix-branch — это локальные ветки.

remotes/origin/HEAD -> origin/main, remotes/origin/feature/add-branch-info, и remotes/origin/main — это удалённые ветки.



# Сравниваем ветки


## Сравнить ветки — git diff <название_ветки1> <название_ветки2>


Вернитесь к проекту git-branches. 

Перейдите в основную ветку через git checkout. 

Откройте файл README.md и добавьте пункт про команду git branch. Файл получится таким.


```
# Ветки в Git 

Чтобы посмотреть все активные ветки в проекте, нужно вызвать команду `git branch` без аргументов. 

```


Сохраните файл, добавьте изменения в staging area, а затем выполните коммит: git add . && git commit -m "Добавить git branch в README".
 
Создайте ветку feature/diff и перейдите в неё. 

Снова откройте файл README.md и добавьте туда новую строку. Должен получиться такой текст.


```
# Ветки в Git 

Чтобы посмотреть все активные ветки в проекте, нужно вызвать команду `git branch` без аргументов. 

Для сравнения веток есть команда `git diff`.

```

Подготовьте файл к сохранению и сделайте коммит: git add . && git commit -m "Добавить git diff в README".

Теперь используйте команду git diff main feature/diff (или git diff master feature/diff), чтобы вывести разницу между двумя ветками. 

Вы увидите точно такой же вывод, как если бы сравнивали два коммита между собой.


```
$ git diff main feature/diff # сравнили ветки main и feature/diff

diff --git a/README.md b/README.md
index 86b1ff4..fff4920 100644
--- a/README.md
+++ b/README.md
@@ -1,3 +1,5 @@

 # Ветки в Git 
 
 Чтобы посмотреть все активные ветки в проекте, нужно вызвать команду `git branch` без аргументов.
+
+Для сравнения веток есть команда `git diff`.

```

При сравнении вы также можете использовать название ветки и хеш коммита. 

Для этого сначала выполните команду git log --oneline, чтобы вывести список коммитов.


```
$ git log --oneline

2ea56ab (HEAD -> feature/diff) Добавить git diff в README
de8b09b (main) Добавить git branch в README
7ad18bd Добавить файл README

```

Теперь выполните команду git diff с названием основной ветки и хешем коммита в ветке feature/diff. 

У нас получилась следующая комбинация: git diff main 2ea56ab. У вас параметры могут быть другими.


```
$ git diff main 2ea56ab

# вывод будет такой же, как при использовании git diff main feature/diff

```

Вывод будет такой же, как после выполнения команды git diff main feature/diff. 


Когда вы вызываете git diff <название_ветки1> <название_ветки2>, Git находит два коммита, на которые указывает каждая из веток, и сравнивает их. 

Также с веткой можно сравнивать указатель HEAD.


А вот как схематически выглядит ваш проект git-branches после всех изменений.


[результат](https://pictures.s3.yandex.net/resources/M3_T3-3_1687851357.png)


## Суффикс навигации ~


Сравнивать хеши комитов может быть неудобно, ведь в одной ветке их может быть много. 


Представьте: сначала вы выводите историю через git log, затем ищете в длинном списке хеши тех коммитов, которые хотите сравнить,

и только потом выполняете git diff.


Для облегчения этой задачи в Git есть суффикс навигации ~N, где N — это число. 

Он отсчитывает от заданного коммита N коммитов назад во времени. 

Нумерация начинается с нуля: commit~0 — это сам коммит, commit~1 — предыдущий, commit~2 — предшествующий предыдущему и так далее.

Например, HEAD~1 — это следующий за текущим коммит. А main~5 — это пятый коммит в ветке main, если считать с последнего выполненного коммита.

На практике чаще нужен либо текущий коммит (HEAD), либо следующий за ним (HEAD~1). Для ~1 есть специальное сокращение ~ (без числа). 

То есть вместо HEAD~1 обычно пишут просто HEAD~.





