# «Облачное хранилище»

## Описание
В рамках проекта была поставлена задача разработать REST-интерфейс для загрузки файлов и отображения списка уже загруженных пользователем файлов. 

Все запросы к этому сервису должны проходить авторизацию, что гарантирует безопасность данных. При этом заранее подготовленное веб-приложение (FRONT) должно иметь возможность подключаться к разработанному сервису без необходимости в доработках. Кроме того, функционал FRONT должен использоваться для авторизации пользователей, загрузки файлов и вывода списка загруженных файлов.

## Технологический стек
1. Spring Boot.
2. Maven.
3. Docker, Docker Compose.
4. GitHub.
5. Unit-тесты, mockito.
6. Testcontainers.

## Запуск FRONT приложения
Репозиторий фронтенд-приложения доступен в папке `frontend`. Для его запуска необходимо выполнить несколько шагов:

1. Скачать репозиторий и распаковать его в локальную папку. 
2. Установить [Node.js](https://nodejs.org/en/download/current) (не ниже 19.7.0). 
3. Задать URL для обращения к бэкенд-сервису, установив переменную `VUE_APP_BASE_URL` в файле `.env` следующим образом: `http://localhost:9090`. 
4. Перейти в папку FRONT и выполнить команды `npm install`, а затем `npm run serve`. В результате FRONT  будет доступен по адресу `http://localhost:8080/` и сможет отправлять запросы к REST-сервису по адресу `http://localhost:9090/`.

## Запуск REST приложения
Для запуска приложения используются команды Docker. 
1. Скачать или склонировать репозиторий приложения. 
2. Изменить имя пользователя и пароль к БД в файлах `application.properties` и `docker-compose.yml`. 
3. Упаковать в Maven.
4. В терминале создать образ приложения `docker build -t app:latest .`
5. Упаковать образ в контейнер с помощью команды `docker-compose build`. 
6. Запустить контейнер `docker-compose up`.
7. Для остановки приложения нажать комбинацию клавиш Ctrl+C.

## База данных
Содержит данных пользователей:
| Логин | Пароль | Роль |
|---------------------|-------|-----|
| Grisha | superAdmin | ROLE_ADMIN |
| Vika | user1 | ROLE_USER | 