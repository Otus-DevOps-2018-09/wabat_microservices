## wabat_microservices
[![Build Status](https://travis-ci.com/Otus-DevOps-2018-09/wabat_microservices.svg?branch=master)](https://travis-ci.com/Otus-DevOps-2018-09/wabat_microservices)

wabat microservices repository

### docker-1
<details>
<summary>docker format output</summary>


``` docker inspect <_id>```
выдает массив json, описывающий все параметры <u_container_id> или <u_image_id>

ключ --format= [c другими опциями](https://docs.docker.com/v17.09/engine/admin/formatting/#template-functions)

docker использует [go templates](https://golang.org/pkg/text/template/) для форматирования вывода

</details>

### docker-2

<details>
<summary>docker container</summary>

docker mashine - инструмент для управления машинами с dcoker 

docker run --pid 

по умолчанию PID namespace контейнера включен, 
ключ --pid используется для управления PID namespace контейнера, для включения в namespace другого контейнера или хоста на котором он  запущен 


[namespaces](https://blog.selectel.ru/mexanizmy-kontejnerizacii-namespaces/)

</details>

### docker-3

<details>
<summary>Сбрка образов</summary>

#### Рекомендации
- создавать эфемерные контейнеры со statless приложениями
- использовать отдельные директории для build context
- использовать .dockerignore на манер .gitignore

#### Оптимизация размера
- не устанавливать не нужные пакеты
- использовать multistage builds
- собирать аргументы инструкции RUN

</details>

### docker-4

<details>
<summary>Сети docker, docker-compose</summary>

#### Сети docker
типы сетевых драйверов:
- bridge (default)
- host
- none
- macvlan 
- 3rd party

[подробнее тут](https://success.docker.com/article/networking)

#### docker-compose

позволяет составлять список инструкций и создавать комплексные окружения, управлять процессом сборки и запуска сервисов.

по умолчанию docker compose читает два файла docker-compose.yaml и docker-compose.override.yaml,
переопределить которые можно другими файлами следующими после ключа -f при старте, при этом каждый последующий будет переопределять предыдущий 

считается что на каждую версию приложения нужно собирать образ [заново](https://stackoverflow.com/questions/52689570/how-to-change-source-code-without-rebuilding-image-in-docker)

</details>
