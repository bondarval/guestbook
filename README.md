# Conference Guestbook
## Описание
### Общие замечания
Учебный проект PHP Symfony. 
Предназначен для практического знакомства с основными принципами построения веб-приложения на PHP с помощью фреймворка Symfony. 
За основу взята официальная документация, в частности, проект, описанный в книге Symfony 5: The Fast Track.
Проект представляет собой сайт-гостевую книгу, предназначенную для сбора отзывов о конференциях с возможностью прикрепления изображений к сообщениям. 
Регистрация на сайте для написания комментария не требуется, однако сообщения проходят автоматизированную проверку на спам и модерацию перед размещением на сайте.
### Технические особенности
Для обеспечения рабоотоспособности инфрастуктуры используется контейнеризация Docker, в частности для развертывания базы данных приложения (PostgreSQL) 
Предусмотрена возможность использовать SPA для мобильных устройств под управлением Android.
Также работает API для конференций и комментариев, реализованный с помощью API Platform.
Реализована возможность получения уведомлений (для администраторов) по электронной почте и каналам Slack, необходимо настраивать соответствующие переменные окружения.
Для хранения данных о сессиях используется Redis, в качестве брокера сообщений - RabbitMQ.
Для автоматизированной проверки на спам необходима учетная запись Akismet и ключ Akismet API.
Проект подготовлен для развертывания в облаке Platform.sh, однако, по техническим причинам, развернут там не был.
## Используемые технологии
- PHP 8.1
- Symfony 5.4
- PostgreSQL 13
- Redis
- RabbitMQ
- Docker
- API Platform
- PHPUnit
- Varnish
- Webpack Encore
- Preact
- Cordova
- Подробнее см. зависимости в composer.json и package.json
## Развертывание проекта
Клонировать проект:
```bash
$ git clone git@github.com:bondarval/guestbook.git
```
Установить зависимости:
```bash
$ composer install
```
Для локального развертывания проекта необходимо запустить контейнеры Docker:
```bash
$ docker-compose up -d
```
Для запуска локального сервера проекта достаточно выполнить команды(с логированием):
```bash
$ symfony serve
$ symfony open:local
```
или запустить сервер в фоновом режиме:
```bash
$ symfony server:start -d
$ symfony open:local
```
При необходимости запустить тесты, выполнить команду:
```bash
$ make tests
```
Перенести в базу данных тестовые данные можно с помощью команд:
```bash
$ docker-compose exec database psql -U postgres -d postgres
$ docker-compose exec database psql < dump.sql
```
## Автор
- Бондарь Валерий

