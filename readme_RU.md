# ShizzaHo WebOS documentation

**Система является лишь пародией на настоящую ОС, это лишь игрушка для разработчика :)**

## Запуск системы

Перед запуском системы убедитесь что на вашем ПК установлен NodeJS

Также не забудьте выполнить установку зависимостей: ``npm install``

Запуск системы в обычном режиме: ``npm start``

Запуск системы в режиме разработчика: ``npm run dev``

Опционально можно дописать порт через пробел, по умолчанию порт будет 3000

После запуска можете переходить к системе, она открывается по адресу: [http://localhost:3000](http://localhost:3000)

## Работа системы

Весь низкий уровень системы находится в папке **core**, в исключение идет папка **public**, там находится уже высокий уровень.

Низкий уровень отвечает за работу с настоящей системой (файлы, информация и прочее), с хостом (express.js) и прочим...

![image](docs/runningthehost.png)

Переходным звеном между низким и высоким уровнем играет скрипт расположенный в  **public/scripts/core/index.js**, он отвечает за общение с низким уровнем, он отправляет и получает запросы от низкого уровня, хранит в себе необходимые системные переменные, методы необходимые для работы системы (работа с файлами, запуск программм, подключение библиотек, и прочее).

из этого скрипта также запускаются системные модули, такие как **hello** который играет роль ппрограмммы-приветствия и финальной настройки ОС (подгружает библиотеки, присваивает системные переменные), а также запускает консоль, и  **console**, который обеспечивает отображение системной консоли на экране.

## Работа пользовательских программ

программа для **ShizzaHo WebOS** располагается в обыкновенном JS файле, но чтобы программа начала работать, необходимо выполнить несколько условий:

* программа всегда пишется в ES6+ Class, это условие системы, которое необходимо соблюдать.
* При запуске программмы она должна создавать экземпляр своего класса.
* Название класса оформляется в следующем формате: ``СистемныйСтатус_Автор_Название``, например: ``System_ShizzaHo_Hello``, это не обязательно, но рекомендуется для характеризации программм.

Запускаясь, в системе устанавливается новое значение переменной **openProgramPath**, в нее помещается путь до вашей программмы, это можно использовать для подключения других скриптов, или запуска другой программмы из каталога, пример программмы есть в стандартной поставке системы, найти программму можно по пути: **memory/dev/simple_app/index.js**

Запуск пользовательских программм осуществляется через стандартный метод в JavaScript: **eval()**

## Библиотеки

Система поддерживает подключение сторонних библиотек, как пример, одной из стандартных библиотек является **ShizzaHo_GUI**.

Библиотеки сканируются при запуске систем, и загружаются в системную переменную **libraries**.

Библиотеки распологаются по пути в: **memory/system/libraries**

Пример для создания бибилиотеки можно найти по пути: **memory/dev/simple_library/index.js**

Библиотека в отличии от программ, работает совершенно иначе, библиотека в понимании **ShizzaHo WebOS** это набор методов которые выполняют какую-то определенную задачу, эти методы оборачиваются в объект и возвращаются по методу **return**.

Помимо этого существует два обязательных метода **start** и **stop**, они необходимы для разработчиков, которые будут использовать вашу библиотеку в своих программах, метод **start** будет выполнять роль конструктора, который будет выполнять необходимые для вашей библиотеки действия, метод **stop** необходим для завершения работы вашей библиотеки.

## Скриншоты

![image](docs/screen_1.png)

![image](docs/screen_2.png)

## Другое

[Системные команды](docs/ru/system_command.md)