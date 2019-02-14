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

### gitlab-ci-1

<details>
<summary>Устройство Gitlab CI. Построение процесса непрерывной интеграции</summary>

[рекомендации по подбору сервера](https://docs.gitlab.com/ce/install/requirements.html)

в проекте может быть определен CI/CD пайплайн, задачи (jobs) входящие в пайплайн должны исполняться на runners, установку и регистрацию которых можно производить [в ручную](https://docs.gitlab.com/runner/install/) или автоматически, например при помощи [ansible-gitlab-runner](https://github.com/haroldb/ansible-gitlab-runner)

настроить интеграцию со slack можно при помощи web-hook в Project > Settings > Integrations > Slack notifications

</details>

### gitlab-ci-2

<details>
<summary>Непрерывная поставка с Gitlab CI</summary>

Схема непрерывной поставки:

1) сервера gitlab

2) runners (установленных локально на сервере gitlab)
- docker executor, с дефлтным базовым образом gitlab/gitlab-runner:latest, запускающим задания без тега
- shell executor, запускающий задания с тегом `ansible` в контейнере с установленным ansible; [dockerfile](https://github.com/Otus-DevOps-2018-09/wabat_microservices/tree/master/gitlab-ci/continious-delivery/alpine-ansible-runner/Dockerfile)

для работы с динамическими окружениями необходимо: 

указать в ansible.cfg пользователя, приватный ключ, путь к инвентарному скрипту; 
ключи-ssh; 
файлы с учетными данными и скрипт gce.py монтируются к контейнеру к папке /etc/ansible/inventory;


3) ansible-playbooks: 
- выполняющихся для создания/удаления инстансов
- выполняющиеся на созданных инстансах для установки среды и самого приложения (docker, git clone)

Файлы playbook находятся в директории gitlab-ci/continious-delivery/ansible-playbooks.

***
Схема реализована на основе Google Cloud Platform и динамического инвентарного скрипта gce.py.
В vars.yml необходимо заполнить переменные:

из файла ключа Сервисные аккаунта в проекте GCE,

ключ-ssh для создаваемых инстансов,

а так же имя этого инстанса.

</details>


