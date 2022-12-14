# **Git** - что ты такое?

![картинка](teatop_pict.png)

*Git* - это программа помощник, которая хранит и показывает все измениня внесенные в файл. Т.е. она не сохраняет каждый раз *1000* копий нашего файла, а лишь хранит исходную версию и все ее изменения.

*Репозиторий* - это папка, в которой *Git* отслеживает изменения. На компьютере может быть любое количество репозиториев, каждое из которых хранится в собственной папке. 

Каждый репозиторий *Git* в системе является независимым, поэтому изменения, сохраненные в одном репозитории, не влияют на содержимое другого.

# Основные команды в **Git**
* **git init** - Инициализация работы git. Т.е. делает из папки репозиторий. Каждый раз, когда мы начинаем работу с новым файлом необходимо для начала его инициализировать.
* **git status** - Показывает статус папки.
* **git add name.file** - Сохраняем наш файл для отслеживания git-ом. Где *name.file* - это имя файла, с которым мы работаем.
* **git commit -m "name.commit"** - Сохраняем внесенные изменения (коммит). Где *name.commit* - это название коммита.
Коммиты принято указывать на английском языке. Они должны быть краткие, емкие и полностью отображать суть внесенного изменения. 
Первый коммит обычно называют *First commit* или *Initial commit*.
* **git log** - Вызывает журнал изменений. Их может быть много, поэтому в терминале обычно выводятся 2 последних. Если прокрутить их, то можно увидеть все.
* **git checkout commit** - Дает возможность перейти к конкретному изменению. Где *commit* - это числовой идентификатор коммита, можно ввести 4 первые уникальные цифры идентификатора коммита  и он автоматом перейдет к нему.
* **git checkout master** - Открывает актуальную в(головную) версию файла.
* **git diff** - Показывает изменения в файле. Что мы добавили или удалили.

# Полезные функции в **Git**
* **Ctrl + S** - Сохраняет наши изменения в редакторе файле. Нажимаем всегда, везде и почаще. 
> *Это сочетание клавиш - лучший друг программиста* :point_left: 
* **clear** - Очищает зону терминала.
* **Q** - Возвращает к дальнейшей работе с терминалом, например после просмотра *log*-ов.
* **Ctrl + ~** - Переключает между из окна ввода текста в окно терминала или обратно.

*NB* - чтобы не натыкаться на постоянное забывчивость при нажатии Ctrl+S функционал git предусматривает возможность автосохранения. Это можно сделать в панели задач *<Файл-Автосохранение>*.


Вот, для примера, еще некоторые полезные команды

![Полезные комманды в git](useful_commands.jpeg)


# Алгоритм из 4-х обязательных шагов работы с файлами
1. Вносим изменения в поле ввода текста;
2. ***Ctrl + S*** - сохраняем наши изменения;
3. ***git add <name.file>*** -  добавляем в *git* наши изменения;
4. ***git commit -m <name.commit>***  - присваиваем нашим изменениям название.

# Ветвление в __*git*__
## Создание веток
__*git branch*__ - команда, для отслеживания существующих веток.

__*git branch <name.branch*>__ - команда для создания новой ветки.

__*git checkout <name.branch>*__ - команда, позволяющая перейти на нужную ветку.
## Слияние веток

__*git merge <name.branch>*__ - команда для слияния веток. Где <name.branch> - это имя ветки, которую мы должны слить с веткой master.

__*NB*__ -  слияние происходит из ветки master. Т.е. сначала мы должны перейти в ветку master, затем исполнить команду *git branch <name.branch>*.

Если побочная ветка (которую мы слили в master) нам больше не нужна, то мы можем ее удалить. Но и все логи по ней также удалятся.

__*git branch -d <name.branch>*__ - команда, удаляющая ветку.

Существует несколько типов слияния веток:

* _Fast-Forward_ - стратегия слияния веток, при которой происходит автоматическое добавление изменений из вливаемой ветки в основную. Тот случай когда ветка master отстала по коммитам от вливаемой в нее ветки, тем самым мы просто обновляем содержимое в ветке master.
* _Ort-Strategy_ - Когда ветки master и вливаемая в нее ветка развивались по отдельности (параллельно), но изменения вносимые из вливаемой ветки не затрагивают изменения по ветке master.
* _Conflict_ - Ситуация, при которой вливаемая информация конфликтует с уже существующей в ветке master.

## Конфликты
Конфликты в *git* могут возникнуть при слиянии двух веток. В том случае, если в ветке master, на момент слияния, находится текст отличный от вливаемого в него дополнения. 
Для дальнейшей работы в ветке master, необходимо разрешить создавшийся конфликт. 

Это можно сделать несколькими способами:

* _Accept current change_ - Принять текущие изменения (оставить то, что на данный момент в ветке master);
* _Accept incomming change_ - Принять входящие изменения (оставить то, что во вливаемом файле);
* _Accept both chenges_ - Принять оба предложения на изменения (и произвети корректировку вручную);
* _Compare changes_ - Сравнить изменения

## Антипаттерны работы с git
В git не принято добавлять большие файлы, типа фото. Он постонно их игнорит. 

Например: 

У нас есть фото, мы не хотим сохранять его в git. При этом не хотим, чтобы оно висело в неотслеживаемых файлах и git постоянно ругался. 

Мы можем создать отдельный файл с названием .gitignore (точка перед именем обязтельна).
В этом файле укажем имя и расшиварение нашего файла (фото).

Все, что мы добавили в этот файл git будет автоматически игнорировать. 

__*Этот файл обязательно должен находится в ветке master!!!*__

## Работа с удалёнными репозиториями

Если при работе с локальными репозиториями (теми, что хранятся на нашем компьютере) для начала работы с git мы начинали с инициализации (*git init*), сохраняли файл, добавляли новые ветки, коммитили - и это все было доступно только нам.

То в современных реалиях, большие компании и большие команды работают с удаленными репозиториями на спец. серверах.

Одним из таких являетсяя [Github](https://github.com/)

## Переносим удалённый репозиторий на наш ПК.

1. Создадим новую папку на нашем ПК. 
2. Преходим на сайт [Github](https://github.com/) и через поиск ищем нужный репозиторий, проваливаемся в него. Справа будет зеленая кнопка **CODE**, нажжимаем ее и копируем URL-адрес.
3. Возвращаемся в VSC и в окне терминала открываем удалённый репоиторий с помощью команды 

    __*git clone*__ <ссылка на удаленный репозиторий>

4. Удаленный репозиторий скопировался на наш ПК. Т.е. он скачал папку с таким же названием, как назывался репозиторий на Github и все файлы, которые в него входили.

 :heavy_exclamation_mark: :heavy_exclamation_mark: :heavy_exclamation_mark: Если мы на этом этапе проверим статус файла (*git status*), то выпадет ошибка о том, что репозиторий не создан. Так как по факту, мы находимся в нашей созданной локально папке, а не в сохраненнном репозитории. 
 
 5. Перейдем в нужную директорию с помощью команды 

 __*cd <название удалённого репозитория>*__


## Превращаем локальный репозиторий в удаленный

1. Создадим новую папку на нашем ПК.
2. Инициализируем ее работу (*git init*)
3. Создадим новый файл, поработаем в нем, сохраним, закоммитим.
5. Перейдем на сайт  [Github](https://github.com/). В правом верхнем углу (рядом с нашим профилем) нажимаем ":heavy_plus_sign:"
6. Выбираем "*New repository*"
7. Присваиваем имя нашему новому репозиторию. Все остальные параметры пока оставляем по умолчанию.
8. Создаем новый репозиторий "*Create new repository*".

Github предложит 3 варианта продолжения работы с репозиторием:

* Можно создать новый файл через терминал и начать с ним работать там;
* Можно уже существующий репозиторий привязать к этому удаленному репозиторию;
* Либо импортировать код из другого репозитория.

Так как у нас уже есть локальный репозиторий, который мы хотим отправить в интернет, значит нам нужно следовать по второму варианту.

9. Копируем необходимые команды прямо с сайта и вставляем их в терминал VSC.
10. Посмотрим, что изменилось в нашем репозитории на Github. Обновим страницу.

Если мы работаем в команде из нескольких человек или хотим передать (отправить кому-то то, что мы сделали в нашем репозитории) - то мы можем отправить просто ссылочку на наш удаленный репозиторий.

## Рассмотрим ситуацию постоянной работы с удаленным репозиторием.

При работе в VSC мы постоянно вносим изменения в наш файл локального репозитория, сохраняем, коммитим, создаем новые ветки. 
Стобы наши изменения отобразились на удалённом репозитории нужна компанда:

__*git push*__
 
> *Push* - с англ. толкать, значит мы толкаем наш файл на Github.

также можно изменять файл не только на своем компьютере, но и напрямую на сайте [Github](https://github.com/). 

В поле терминала нажимаем ":pencil2:"

Внесем необходимые изменения в тексте.

Ниже, в специальном окошке, создадим коммит. 

Вауля, теперь на Gitbub более актуальная версия, чем на нашем ПК.

Что же делать? Просто обновим наш локальный репозиторий с помощью команды:

__*git pull*__

> *Pull* - с англ. тянуть, значит мы стягиваем актуальную версию с Github.

## Pull request  - или запрос на вливание каких-либо изменений в чужой репозиторий

Чтобы поучаствовать в другом репозитории/проекте с "открытым кодом" (Open Source projects) необходимо создать его копию на нашем аккаунте. Это делается с помощью кнопки "FORK".

>*Fork* - с англ. переводится как вилка. В среде программистов это действие называют *форкнуть*.

Когда мы форкаем чужой репозиторий, у него появляется ответвление. 
Дальше нам нужно сохранить себе на локальный компьютер это репозиторий (*git clone <ссылка на репозиторий>*).

:heavy_exclamation_mark: Чтобы продолжить работу с этим файлом и в дальнейшем предложить изменения владельцу репозитория необходимо создать отдельную ветку. Все что мы будем делать, будем делать только в этой ветке.

Внесем желаемые изменения в файл, сохраним, закоммитим.

Теперь у нас есть новая ветка и в ней находится вся информация, которую мы хотим предложить хозяину репозитория. 

Отправим изменения на Github также с помощью команды *git push*. В этот момент git может поругаться и предложит дополненную команду. Мы с ним согласимся. Скопируем предложенную команду и введем ее в терминале.

Перейдем на сайт Github. Обновим страницу.

У нас должна появится новая возможность "__*Compare and pull request*__".

> *Compare and pull request* - с англ. переводится как сравнить и притянуть запрос. 

Нажимаем ее. 

В открывшемся окошке следует добавить описание нашего предложения. Чтобы исходный хозяин репозитория понимал, что мы ему предлагаем.

### *P.S. Кратко подитожим работу с удалёнными репозиториями.*

:point_right: Чтобы залить удаленный репозиторий на наш локальный ПК:

* Находим URL-репозитория, копируем адрес

*  "Клонируем" его себе на ПК через команду *git clone*

* Переходим в нужную директорию через команду cd 

:point_right: Чтобы отправить локальный репозиторий на Github:

* Создаем новый репозиторий на Github

* Копируем необходимые команды

* Вводим их в терминале VSC

* Командой *git push* отправляем изменения на Github

* Командой *git pull* стягиваем изменения с Github

:point_right: Pull request:

* Fork-аем нужный репозиторий на Github

* Командой *git clone* сохраняем его копию на наш ПК

* Создаем отдельную новую ветку. Работаем только в ней

* Сохраняе, коммитим

* Командой *git push* отправляем изменения на Github

* Делаем *Compare and pull request* с основным репозиторием

* Не забываем добавлять описание к нашим предложенным изменениям. 
## Полезные ссылки по теме:
* [Git для новичков (часть 1)](https://habr.com/ru/post/541258/)
* [Git для новичков (часть 2)](https://habr.com/ru/post/542616/)
* [Настройка репозитория](https://www.atlassian.com/ru/git/tutorials/setting-up-a-repository)
* [Сохранение изменений](https://www.atlassian.com/ru/git/tutorials/saving-changes)
* [Проверка репозитория](https://www.atlassian.com/ru/git/tutorials/inspecting-a-repository)
* [Отмена изменений](https://www.atlassian.com/ru/git/tutorials/undoing-changes)
* [Тренажер по Git](https://learngitbranching.js.org/?locale=ru_RU)
* [Шпоргалка по Markdown](https://texterra.ru/blog/ischerpyvayushchaya-shpargalka-po-sintaksisu-razmetki-markdown-na-zametku-avtoram-veb-razrabotchikam.html)