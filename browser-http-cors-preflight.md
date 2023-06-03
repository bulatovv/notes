---
tags: browser, http, cors
---

# Предварительные запросы CORS

Prefligth запрос - специальный запрос, нужный, чтобы понять, понятен ли протокол CORS серверу. Для этого используются специальные методы и заголовки

Это запрос `OPTIONS`, использующий три заголовка запроса HTTP: `Access-Control-Request-Method`, `Access-Control-Request-Headers` и заголовок `Origin`. 

Например, клиент перед отправкой запроса `DELETE` может спросить у сервера, разрешит ли он такой запрос, используя предварительный запрос:
```http
OPTIONS /resource/foo
Access-Control-Request-Method: DELETE
Access-Control-Request-Headers: origin, x-requested-with
Origin: https://foo.bar.org
```

Если сервер разрешает подобный запрос, он оправить ответ
```http
HTTP/1.1 204 No Content
Connection: keep-alive
Access-Control-Allow-Origin: https://foo.bar.org
Access-Control-Allow-Methods: POST, GET, OPTIONS, DELETE
Access-Control-Max-Age: 86400
```

### Простые запросы
Некоторые запросы не провоцируют отправку preflight-request. Они называются простыми запросами. Запрос является простым, если он удовлетворяет следующим условиям:

Используется один из методов
+ `GET`
+ `HEAD`
+ `POST`

Не установлены заголовки кроме
+ `Accept`
+ `Accept-Language`
+ `Content-Language`
+ `Content-Type` **только**
	+ `application/x-www-form-urlencoded`
	+ `multipart/form-data`
	+ `text/plain`