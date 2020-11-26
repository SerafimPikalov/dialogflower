# Dialogflower

Прокси-сервер для подключения [Яндекс Алисы](https://dialogs.yandex.ru/) к [Google Dialogflow](https://cloud.google.com/dialogflow/es/docs).
Позволяет создавать навык средствами Dialogflow, а затем подключить его к Алисе без написания дополнительного кода.

_Создан с помощью [Just AI Conversational Framework](https://just-ai.com/jaicf-framework)_.

## Как использовать

### 1. Создайте агента Dialogflow

Первым делом создайте нового агента на Dialogflow на русском языке, добавив в него нужные вам интенты, сущности и ответы.
Протестируйте его в тестовой консоли Dialogflow.

> Вы можете использовать [ответы для Google Assistant](https://developers.google.com/assistant/conversational/df-asdk/rich-responses) - Dialogflower автоматически сконвертирует их в ответы для Алисы

**Добавьте событие с именем _start_** в стандартный интент _Default Welcome Intent_, чтобы навык Алисы мог запустить диалог.

### 2. Скачайте сервисный аккаунт

- Перейдите в настройки агента (шестеренка рядом с названием)
- Кликните на идентификатор проекта (напротив _Project ID_)
- В левом меню выберите _IAM и администрирование_ > _Сервисные аккаунты_
- Нажмите _Создать сервисный аккаунт_ и укажите любое название для сервисного аккаунта
- Нажмите _Создать_ и выберите роль _Клиент Dialogflow API_
- Нажмите _Продолжить_ и потом _Готово_
- Напротив созданного аккаунта в списке нажмите на три точки и выберите в меню _Создать ключ_
- Выберите _JSON_ и нажмите _Создать_

На ваш компьютер автоматически скачается JSON файл - это и есть **сервисный аккаунт**.

### 3. Скорпируйте OAuth токен

Чтобы в Алисе работали картинки, которые можно добавлять в Dialogflow, нужно получить OAuth токен.
Для этого просто [пройдите по этой ссылке](https://oauth.yandex.ru/authorize?response_type=token&client_id=c473ca268cd749d3a8371351a8f2bcbd) и скопируйте ваш токен.

### 4. Запустите Dialogflower

Ваш экземпляр Dialogflower можно запустить в облаке Heroku, просто нажав на кнопку ниже.

- При запуске вставьте в настройках ваш _OAuth токен_ и _содержимое вашего файла JSON с сервисным аккаунтом_
- Нажмите на _Deploy app_
- Через некоторое время, когда ваш сервер будет автоматически запущен, нажмите на _Manage app_ > _Open app_
- Скорпируйте адрес страницы - это вебхук для вашего навыка Алисы

_Нажмите на эту кнопку, чтобы запустить ваш экземлпяр Dialogflower в облаке Heroku_

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### 5. Создайте навык Алисы

- Перейдите в [консоль разработчика навыков Алисы](https://dialogs.yandex.ru/developer) и создайте новый навык
- Вставьте в настройках навыка адрес вашего экземпляра Dialogflower в поле _Webhook URL_
- Перейдите на вкладку _Тестирование_, чтобы протестировать ваш навык

## Обновление контента

Чтобы обновлять контент для вашего навыка, вам нужно просто добавлять новые интенты и ответы в вашем агенте Dialogflow.

## Проблемы и предложения

Если вы столкнулись с какой-либо проблемой или у вас есть идея, пожалуйста [создайте новую задачу здесь](https://github.com/just-ai/dialogflower/issues).