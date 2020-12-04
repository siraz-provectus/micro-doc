<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Данные передаваемые в заголовках (Headers) API](#%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D0%B5-%D0%BF%D0%B5%D1%80%D0%B5%D0%B4%D0%B0%D0%B2%D0%B0%D0%B5%D0%BC%D1%8B%D0%B5-%D0%B2-%D0%B7%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BA%D0%B0%D1%85-headers-api)
- [Ошибки](#%D0%BE%D1%88%D0%B8%D0%B1%D0%BA%D0%B8)
- [Датчик](#%D0%B4%D0%B0%D1%82%D1%87%D0%B8%D0%BA)
  - [Записать данные датчика](#%D0%B7%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D0%B5-%D0%B4%D0%B0%D1%82%D1%87%D0%B8%D0%BA%D0%B0)
- [Прошивка](#%D0%BF%D1%80%D0%BE%D1%88%D0%B8%D0%B2%D0%BA%D0%B0)
  - [Скачать прошивку](#%D1%81%D0%BA%D0%B0%D1%87%D0%B0%D1%82%D1%8C-%D0%BF%D1%80%D0%BE%D1%88%D0%B8%D0%B2%D0%BA%D1%83)

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

## Датчик

### Записать данные датчика
  url: `http://134.0.118.202/api/sensor_data`
  method: POST

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"

    params:

      uid:              '63727tgsg89'        # ID датчика (обязательное поле)
      temperature:      25.5                 # температура (обязательное поле)
      moisture:         73                   # влажность (обязательное поле)
      date:             2020-03-03T14:08:16  # дата и время (обязательное поле)
      firmware_version: 'v1.2.1'             # версия прошивки датчика (необязательное поле, если отсутствует то считаем что версия актуальная)

  Response:

    { "message": "OK" } || { "message": "need_update", "firmware_version": "1.0.1" }

##  Прошивка

### Скачать прошивку
  url: `http://134.0.118.202/api/firmwares/:firmware_type`
  method: GET

  firmware_types = [sensor]

  Request:

    headers:

      Content-Type: "application/json"
      Accept:   "application/json"
      Authorization:  "Bearer Token"

  Response:

    file
