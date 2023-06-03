---
tags: browser, frontend
---

# Браузерная предзагрузка

см . [Preload, prefetch и другие теги](https://habr.com/ru/post/445264/)


## Preload
`<link rel= "preload">` - загрузить ресурс как можно раньше
```html
<link rel="preload" href="/style.css" as="style" />
```
см [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/rel/preload#what_types_of_content_can_be_preloaded)

Когда использовать
+ Загрузка сторонних шрифтов



## Prefetch
`<link rel= "prefetch">` - загрузить ресурс в фоновом режиме
```html
<link rel="prefetch" href="/style.css" as="style" />
```

Когда использовать
+ Ресурсы, которые могут понадобиться на следующих страницах

## Preconnect
`<link rel= "preconnect">` - подключиться к домену заранее (DNS + TCP + TLS)
```html
<link rel= "preconnect" href="https://api.my-app.com" />
```

Когда использовать
+ Для доменов, которые скоро понадобятся для загрузки ресурсов, точный URL которых не известен ([preload](#Preload) подходит лучше, если точный URL известен)
+ Немного ускорить сторонний скрипт или стиль засчет предварительной установки соединения

**Не стоит злоупотреблять preconnect, так как установка и поддержание соединения - дорогостоющая операция как для клиента, так и для сервера.**

## Dns-prefetch
`<link rel= "dns-prefetch">` - выполнить резолвинг домена заранее (DNS)
```html
<link rel= "dns-prefetch" href="https://api.my-app.com" />
```

Когда использовать
+ Для доменов, которые скоро понадобятся для загрузки ресурсов, точный URL которых не известен ([preload](#Preload) подходит лучше, если точный URL известен)
+ Немного ускорить сторонний скрипт или стиль засчет предварительной установки соединения

## Prerender
`<link rel= "prerender">` - загрузить страницу и отобразить ее на невидимой вкладке
```html
<link rel="prerender" href="https://my-app.com/pricing" />
```

Когда использовать
+ Для загрузки страниц, на которые с высокой вероятностью перейдет пользователь


**Плохо поддерживается основными браузерами**