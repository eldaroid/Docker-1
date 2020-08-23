# Docker-1

## Обзор проекта

![alt text](https://github.com/eldaroid/pictures/blob/master/Docker/Docker-1.png)

*Docker-1* - это последний проект в [школе программирования от Сбербанка](https://21-school.ru/) по ветке SysAdmin (DevOps). Цель этого проекта - познакомить студентов с программой Docker и его основными функциями (установить докер, выполнять команды докер-машины, создание собственных контейнеров для собственных приложений и тд.). Этот проект был завершен 12го июля 2020 года и оценен на 125 баллов. Задание: [`docker.en.pdf`](resources/docker.en.pdf)

![alt text](https://github.com/eldaroid/pictures/blob/master/Docker/score.png)

Проект охватывает основы системного администрирования и предлагает множество небольших задач, разделенных на три группы:
1. - [x] 00_how_to_docker (Знакомство с докером)
2. - [x] 01_dockerfiles (Создание Dockerfile)
3. - [x] 02_bonus (Создать полезные image с помощью Dockerfile)

## Что такое Докер?

Докер - это инструмент, который позволяет разработчикам, системными администраторам и другим специалистам деплоить их приложения в песочнице (которые называются контейнерами), для запуска на целевой операционной системе, например, Linux. Ключевое преимущество Докера в том, что он позволяет пользователям упаковать приложение со всеми его зависимостями в стандартизированный модуль для разработки. В отличие от виртуальных машин, контейнеры не создают такой дополнительной нагрузки, поэтому с ними можно использовать систему и ресурсы более эффективно.

### `00_how_to_docker`

01 \
https://docs.docker.com/machine/reference/create/

02 \
https://docs.docker.com/machine/reference/ip/

03 \
https://docs.docker.com/machine/reference/env/

04 \
https://docs.docker.com/engine/reference/commandline/pull/

05 06 \
https://docs.docker.com/engine/reference/commandline/run/

07 \
https://docs.docker.com/engine/reference/commandline/inspect/

08 \
https://docs.docker.com/engine/reference/commandline/run/

10 11 \
https://docs.docker.com/engine/reference/commandline/volume/

12 \
https://docs.docker.com/engine/reference/commandline/run/ \
https://docs.docker.com/samples/library/mysql/

13 \
https://docs.docker.com/engine/reference/commandline/exec/

14 \
https://docs.docker.com/engine/reference/commandline/run/

15 \
https://hub.docker.com/r/phpmyadmin/phpmyadmin/

16 \
https://docs.docker.com/engine/reference/commandline/logs/

17 \
https://docs.docker.com/engine/reference/commandline/ps/

18 \
https://docs.docker.com/engine/reference/commandline/restart/

19 \
https://docs.docker.com/engine/reference/commandline/run/ \
https://docs.docker.com/engine/reference/commandline/exec/ \
http://flask.pocoo.org/

20 \
https://docs.docker.com/engine/reference/commandline/swarm/ \
https://docs.docker.com/engine/reference/commandline/swarm_init/ \

21 \
https://docs.docker.com/machine/reference/create/

22 \
https://docs.docker.com/engine/reference/commandline/swarm_join-token/

23 \
https://docs.docker.com/engine/reference/commandline/network_create/

24 \
https://docs.docker.com/engine/reference/commandline/service_create/ \
https://docs.docker.com/samples/library/rabbitmq/

25 \
https://docs.docker.com/engine/reference/commandline/service_ls/

26 \
https://docs.docker.com/engine/reference/commandline/service_create/

27 \
https://docs.docker.com/engine/reference/commandline/service_logs/ \
https://docs.docker.com/engine/reference/commandline/service_create/

27 \
https://docs.docker.com/engine/reference/commandline/service_logs/

28 \
https://docs.docker.com/engine/reference/commandline/service_create/

29 \
https://docs.docker.com/engine/reference/commandline/service_ps/

30 \
https://docs.docker.com/engine/reference/commandline/service_scale/

31 \
https://docs.docker.com/engine/reference/commandline/swarm_leave/

32 \
https://docs.docker.com/engine/reference/commandline/rm/ \
https://docs.docker.com/engine/reference/commandline/ps/

33 \
https://docs.docker.com/engine/reference/commandline/rmi/ \
https://docs.docker.com/engine/reference/commandline/images/

34 \
https://docs.docker.com/engine/reference/commandline/rm/

### `01_dockerfiles`

https://docs.docker.com/engine/reference/builder/ \
https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
