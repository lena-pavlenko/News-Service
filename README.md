# News Service
Сервис вывода и поиска новостей

## Описание
Вывод новостей и поиск статей по ключевому слову с помощью [News API](https://newsapi.org/)

### Было реализовано

- Вывод статей (в запросе в качестве страны указана Россия)
- Поиск статей по ключевому слову (поиск осуществляется по всем категориям и странам)

## Стек разработки
Сервис разработан на Vue.js 3 с компонентным подходом

- Vue3
- JavaScript
- [Axios](https://axios-http.com/ru/)
- HTML5
- SCSS
- [Materialize](https://materializecss.com/)
- Git
- REST API

## Запуск проекта
```
npm install
```

### Компиляция и горячая перезагрузка для разработки
```
npm run serve
```

### Компиляция и минификация для продакшена
```
npm run build
```

Для запуска демонстрации сервиса, необходимо иметь **апи-ключ**, получить его можно на сайте [News API](https://newsapi.org/)

### Пример запроса
```js
const response = await axios.get(`https://newsapi.org/v2/top-headlines?country=us&apiKey=YOUR_API_KEY`)
```


### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## Контакты

[Елена Павленко](https://t.me/lenapavlenko) — Frontend Developer