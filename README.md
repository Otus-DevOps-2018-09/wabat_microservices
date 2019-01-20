## wabat_microservices
[![Build Status](https://travis-ci.com/Otus-DevOps-2018-09/wabat_microservices.svg?branch=master)](https://travis-ci.com/Otus-DevOps-2018-09/wabat_microservices)

(https://travis-ci.com/Otus-DevOps-2018-09/wabat_infra.svg?branch=master)](https://travis-ci.com/Otus-DevOps-2018-09/wabat_infra)

wabat microservices repository

### docker-1
<details>
<summary>docker format output</summary>


``` docker inspect <_id>```
выдает массив json, описывающий все параметры <u_container_id> или <u_image_id>

ключ --format= [c другими опциями](https://docs.docker.com/v17.09/engine/admin/formatting/#template-functions)

docker использует [go templates](https://golang.org/pkg/text/template/) для форматирования вывода

</detail>

### docker-2
<details>
<summary>docker container</summary>

docker mashine - инструмент для управления машинами с dcoker 

docker run --rm -ti tehbilly/htop
docker run --rm --pid host -ti tehbilly/htop
по умолчанию PID namespace контейнера включен, 
ключ --pid используется для управления PID namespace контейнера, для включения в namespace другого контейнера или хоста на котором он  запущен 


[namespaces](https://blog.selectel.ru/mexanizmy-kontejnerizacii-namespaces/)

</details>
