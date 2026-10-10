# Commands docker
### containers
<details>

```
docker ps -q | wc -l   - узнать сколько контейнеров рабоает на хосте
```
```
docker ps              — показывает только запущенные контейнеры.
-q                     — выводит только их ID.
wc -l                  — считает количество строк, то есть контейнеров.
```
```
docker ps              — список работающих контейнеров
docker ps -a           — все контейнеры, включая остановленные
docker ps -aq | wc -l  — общее количество контейнеров
docker info            — общая информация о Docker-хосте
```

</details>

### Start container
<details>

```
docker run -d --name my-redis redis   - запустить контейнер из образа Redis

**Важно:** эта команда запускает Redis внутри Docker, но не публикует порт для подключения с хоста.

docker run            — создать и запустить контейнер.
-d                    — запустить в фоновом режиме.
--name my-redis       — задать имя контейнера.
redis                 — имя образа.
```
нужен доступ к Redis с хоста, используй  
`docker run -d --name my-redis -p 127.0.0.1:6379:6379 redis`

</details>

### Stop conteiner
`docker stop app`

### Узнать состояние контейнера
<details>
узнать состояние остановленного alpine контейнера:  
`docker ps -a --filter ancestor=alpine`  
```
Необходимо извлечь изображение Docker, которое будет использоваться для запуска контейнера позже. Извлеките изображение nginx:1.28-alpin
docker pull nginx:1.28-alpine   - скачать образ
docker images                   - проверить что образ скачан
```

</details>

### images
<details>

```
docker images -q | sort -u | wc -l   - сколько образов доступно на хосте
```
```
docker images -q — выводит ID образов.
sort -u — убирает повторяющиеся ID.
wc -l — считает количество уникальных образов.
```
```
docker images       # список образов
docker image ls     # то же самое
docker image ls -a  # включая промежуточные образы
```
docker rmi ubuntu      - удалить образ  
docker rm image alpine - удалить образ  

</details>

### Узнать какой образ используется для ...
<details>
узнать какой образ(image) используется для запуска контейнера nginx-1:
`docker inspect nginx-1 --format '{{.Config.Image}}'`

узнать как называется контейнер, созданный с помощью образа ubuntu:
`docker ps -a`

узнать как называется контейнер, созданный с помощью образа ubuntu:
`docker ps -a --filter ancestor=ubuntu --format '{{.Names}}'`

Чтобы вывести только ID остановленных контейнеров с образом alpine:
`docker ps -a --filter ancestor=alpine --filter status=exited --format '{{.ID}}'`


Чтобы узнать ID остановленного контейнера, использующего образ alpine:
`docker ps -a --filter ancestor=alpine`

</details>


