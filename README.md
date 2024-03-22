# CI/CD. Семинар 01

## Задача
1. Зарегистрироваться на gitlab.com
2. Создать pipeline и runner
3. Попробовать сохранить артефакт одной из стадий + исключить из папки с артефактами любой файл
4. Попробовать сделать любую gitlab pages

## Решение
1. Уже был зарегистрирован, пользоваться возможно только через VPN.
2. Файл .gitlab-ci.yml 

```yaml
image: alpine:latest

pages:
  stage: deploy
  script:
  - echo 'First page 01'
  - mkdir .public
  - cp -r * .public
  - mv .public public
  artifacts:
    paths:
    - public
    exclude:
    - public/file_to_exclude.md
  only:
  - master

```
Gitlab Runner развернут на виртуальной машине, запущен для проекта. Статус: passed.

2. Исключение файла из папки с артефактами:
```yaml
...
  artifacts:
    paths:
    - public
    exclude:
    - public/file_to_exclude.md
...

```

## Скриншоты

![first gitlab page. project](img/1.png "first gitlab page. project")
![first gitlab page. yaml](img/2.png "first gitlab page. yaml")
![first gitlab page. pipeline passed](img/3.png "first gitlab page. pipeline passed")
![first gitlab page. page folder](img/4.png "first gitlab page. page folder")