# Сохранение результатов работы функции в БД 

На этом практическом занятии вы разберётесь с тем, как создавать кластер в сервисе Yandex Managed Service for PostgreSQL. Вами будет создана функция для проверки доступность сайта yandex.ru, которая будет измерять время ответа. А результаты работы функции мы поместим в базу данных, используя подключение к управляемым БД из функции. Так же запустим триггер-таймер, который будет регулярно производить опрос сервера. 

Будет использованы следующие утилиты и сервисы: 
* Cloud Function.
* Yandex Managed Service for PostgreSQL
* yc — Интерфейс командной строки, CLI [документаця](https://cloud.yandex.ru/docs/cli/quickstart#install).

В папке `steps` содержится последовательность шагов необходимых для настройки решения с соответствующими пояснениями.