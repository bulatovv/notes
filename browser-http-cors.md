---
tags: browser, http, cors
---

# Cross-origin resource sharing

CORS - браузерная технология, которая позволяет предоставлять веб-страницам доступ к ресурсам другого домена

## Источники

Источники идентифицируется
- схемой
- хостом
- портом
Т.е `localhost:8000` и `localhost:5713` - разные источники. `<http://example.com>` и `<https://example.com>` тоже являются разными источниками, т.к различаются во первых схемой, во вторых портами (80 и 443 порты по умолчанию)

## Предварительные запросы (preflight requests)
При выполнении cors-запроса из JavaScript, может быть вызвать [preflight-request](browser-http-cors-preflight)