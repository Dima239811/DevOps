# Инструкция по запуску
## Выполнил: Чекалин Дмитрий 23-СБК-1

Проект состоит из двух сервисов:

- Frontend — пользовательский интерфейс на Angular с Nginx.

- Backend — серверное приложение на Java Spring Boot.

Data — папка для хранения данных, сохраняемых backend.

Все команды необходимо выполнять в терминале из папки devops, где находится файл docker-compose.yml.

### 1. Сборка и запуск контейнеров
Собрать образы и запустить все контейнеры одной командой: `docker compose up -d --build`

Для полной пересборки всех образов без использования кеша:
`docker compose build --no-cache`
`docker compose up -d`

### 2. Остановка контейнеров
Остановить все запущенные контейнеры, сохранив их для последующего запуска:`docker compose stop`

Повторно запустить остановленные контейнеры: `docker compose start`

Остановить и удалить контейнеры и сеть проекта: `docker compose down`

Папка data при этом сохраняется.

### 3. Просмотр контейнеров
Посмотреть состояние контейнеров текущего проекта: `docker compose ps`

### 4. Проверка взаимодействия frontend и backend
Проверить получение сохранённых имён через backend: `docker compose exec frontend wget -qO- http://backend:8080/api/get-names`

Отправить тестовое имя:
`docker compose exec frontend wget -qO- --header="Content-Type: application/json" --post-data="{\"name\":\"Test User\"}" http://backend:8080/api/send-name`
