# URL Shortener

Небольшой сервис для сокращения ссылок.\
Позволяет создавать короткий alias для любой URL, а затем переходить по
нему через обычный GET-запрос.

## Возможности

-   Создание коротких ссылок (POST /url)
-   Генерация случайных alias, если alias не указан
-   Редирект по короткой ссылке (GET /{alias})


------------------------------------------------------------------------

# API

## 1. Создать короткую ссылку

### **POST /url**

#### Пример 1 - с заданным alias

``` json
{
  "url": "https://google.com",
  "alias": "google-short"
}
```

#### Пример 2 - без alias (генерируется автоматически)

``` json
{
  "url": "https://example.com/articles/golang"
}
```


## 2. Перейти по короткой ссылке

### **GET /{alias}**

localhost:8080/google-short\
HTTP 302 → https://google.com

#### Пример - alias не найден

``` json
{
  "status": "error",
  "message": "alias not found"
}
```



# Запуск сервера

``` bash
go run ./cmd/url-shortener/main.go
```

Сервис будет доступен по адресу:\
`http://localhost:8080`
