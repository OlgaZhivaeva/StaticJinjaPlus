# static-jinja-plus

Этот репозиторий позволяет собрать Docker-образы которые используют приложение
StaticJinjaPlus для создания статических сайтов

### Создание Докер-образов на основе ubuntu

Для создания Докер-образов на основе ubuntu используйте [Dockerfile-ubuntu](Dockerfile-ubuntu)

Для использования StaticJinjaPlus версии 0.1.1 выполните команду 
```commandline
docker build -t olgazhivaeva/static-jinja-plus:0.1.1 -f Dockerfile-ubuntu .
```
Для использования StaticJinjaPlus версии 0.1.0 выполните команду
```commandline
docker build --build-arg CHECKSUM=3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444 \
--build-arg STATIC_JINJA_PLUS_VERSION=0.1.0 -t olgazhivaeva/static-jinja-plus:0.1.1 -f Dockerfile-ubuntu .
```

### Создание Докер-образов на основе python

Для создания легких Докер-образов на основе python используйте [Dockerfile-slim](Dockerfile-slim)

Для использования StaticJinjaPlus версии 0.1.1 выполните команду 
```commandline
docker build -t olgazhivaeva/static-jinja-plus:0.1.1-slim -f Dockerfile-slim .
```
Для использования StaticJinjaPlus версии 0.1.0 выполните команду
```commandline
docker build --build-arg CHECKSUM=3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444 \
--build-arg STATIC_JINJA_PLUS_VERSION=0.1.0 -t olgazhivaeva/static-jinja-plus:0.1.1-slim -f Dockerfile-slim .
```

### Создание Докер-образов с использованием самой свежей сборки StaticJinjaPlus

Для создания Докер-образа на основе ubuntu c использованием последнего коммита из main-ветки StaticJinjaPlus
используйте [Dockerfile-ubuntu-develop](Dockerfile-ubuntu-develop)
```commandline
docker build -t olgazhivaeva/static-jinja-plus:develop -f Dockerfile-ubuntu-develop .
```
Для создания лугкого Докер-образа на основе python c использованием последнего коммита из main-ветки StaticJinjaPlus
используйте [Dockerfile-slim-develop](Dockerfile-slim-develop)
```commandline
docker build -t olgazhivaeva/static-jinja-plus:develop-slim -f Dockerfile-slim-develop .
```

### Запуск контейнера

Чтобы запустить контейнер из этих образов, выполните следующую команду:
```commandline
docker run --rm -v $(pwd)/path_to_templates:/templates\
                -v $(pwd)/path_to_build:/build olgazhivaeva/static-jinja-plus:version
```
* path_to_templates - путь до вашей папки с шаблонами
* path_to_build - путь до вашей папки с результатами сборки
* version - версия докер-образа static-jinja-plus