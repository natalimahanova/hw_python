
# Веб-сервис для предсказания хабов на Хабре

Реализован веб-сервис с использованием фреймворка FastAPI, который развернут через docker.

В ML части использовалась ранее обученная модель из файла `linearSVC.pkl`, которая предсказывает подходящий хаб (aka тематика) для текста публикации. К текстам перед предсказанием применялась предобработка (удаление лишних символов и т.п., лемматизация с помощью библиотеки `pymystem3`). Для получившихся лемматизированных текстов производилась векторизация текстов по словам с помощью `tfidfvectorizer.pkl`. Упомянутые piсkle-файлы загружались из Yandex Cloud.

Автор: Карнакова Ксения (МОВС23)


 ## Реализованные методы

`/` - приветственное сообщение на главной странице

`/ping` - проверка доступности сервера

`/predict_text` - предсказание подходящего хаба для одного введенного текста

`/predict_text_from_txt` - предсказание подходящего хаба для одного текста из txt-файла

`/predict_texts_from_csv` - предсказание подходящих хабов для текстов из  csv-файла (в csv-файл добавляется новая колонка с предсказанием хаба для каждой статьи)

<img width="1000" alt="fastapi-habr-img" src="https://github.com/xenahkar/fastapi_habr/assets/144525678/df570504-3192-4b61-9bf1-14e3e27602d6">



## Инструкция по запуску

Сборка контейнера:
```
docker compose build
```

Запуск:
```
docker-compose up
```


В файле .env необходимо указать `REDIS_HOST`, `REDIS_PORT`, `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`‎ и `BUCKET`.


## Видео-демонстрация работы сервиса

https://github.com/xenahkar/HSE_habr/assets/144525678/ef8a3135-633e-4e14-a092-b2a94c39fe3a




