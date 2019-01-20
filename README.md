## wabat_microservices

wabat microservices repository

### docker-1
<details>
<summary>docker format output</summary>


``` docker inspect <_id>```
выдает массив json, описывающий все параметры <u_container_id> или <u_image_id>

ключ --format= [c другими опциями](https://docs.docker.com/v17.09/engine/admin/formatting/#template-functions)

docker использует [go templates](https://golang.org/pkg/text/template/) для форматирования вывада

</detail>
