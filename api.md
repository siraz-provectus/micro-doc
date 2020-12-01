<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Данные передаваемые в заголовках (Headers) API](#%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D0%B5-%D0%BF%D0%B5%D1%80%D0%B5%D0%B4%D0%B0%D0%B2%D0%B0%D0%B5%D0%BC%D1%8B%D0%B5-%D0%B2-%D0%B7%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%B0%D1%85-headers-api)
- [Ошибки](#%D0%BE%D1%88%D0%B8%D0%B1%D0%BA%D0%B8)
- [Проекты](#%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D1%8B)
  - [Список проектов](#%D1%81%D0%BF%D0%B8%D1%81%D0%BE%D0%BA-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%BE%D0%B2)
  - [отдельный проект](#%D0%BE%D1%82%D0%B4%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82)
  - [создать проект](#%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D1%82%D1%8C-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82)
  - [обновить проект](#%D0%BE%D0%B1%D0%BD%D0%BE%D0%B2%D0%B8%D1%82%D1%8C-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82)
  - [Удалиить проект](#%D1%83%D0%B4%D0%B0%D0%BB%D0%B8%D0%B8%D1%82%D1%8C-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Данные передаваемые в заголовках (Headers) API
  * Content-Type:   "application/json"
  * Accept:         "application/json"
  * Authorization:  "Bearer Token"

## Ошибки
  * 422 - Валидационная ошибка
  * 406 - Неверный формат
  * 401 - Не авторизован
  * 400 - не правильный запрос
  * 404 - Запись не найдена

  Формат сообщений об ошибке:

    {
      error: {
        messages: [сообщение 1, сообщение 2],
        fields: [field1, field2]  # Массив пустой если ошибка не относится к специфическому полю
      }
    }

## Проекты

### Список проектов
  url: `http://microclimatic.ru/api/projects`
  method: GET

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"

  Response:

    [
        {
            "id": 1,
            "name": "airnanny",
            "file_url": "http://microclimatic.ru/uploads/projects/1/updates.txt"
        },
        {
            "id": 2,
            "name": "airnanny_dev",
            "file_url": "http://microclimatic.ru/uploads/projects/2/updates.txt"
        }
    ]

### отдельный проект
  url: `http://microclimatic.ru/api/projects/airnanny`
  method: GET

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"

  Response:

    {
        "id": 1,
        "name": "airnanny",
        "file_url": "http://microclimatic.ru/uploads/projects/1/updates.txt"
    }

### создать проект
  url: `http://microclimatic.ru/api/projects`
  method: POST

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"

    params:

    name: 'airnanny_new'       # название проекта (обязательное поле)
    file: file                 # file прошивки

  Response:

    {
        "id": 3,
        "name": "airnanny_new",
        "file_url": "http://microclimatic.ru/uploads/projects/1/updates.txt"
    }

### обновить проект
  url: `http://microclimatic.ru/api/projects/airnanny_new`
  method: PUT

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"

    params:

    file: file                 # file прошивки

  Response:

    {
        "id": 3,
        "name": "airnanny_new",
        "file_url": "http://microclimatic.ru/uploads/projects/1/updates.txt"
    }

### Удалиить проект
  url: `http://microclimatic.ru/api/projects/airnanny_new`
  method: PUT

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"


  Response:

    { message: 'Проект удален'}
