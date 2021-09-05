# Создание Триггера
# Создание Триггера-таймера
Проверять доступность сайта конечно лучше в автоматическом режиме через равные промежутки времени. Для этой задачи создадим триггер-таймер. Он будет использовать крон выражения:

    yc serverless trigger create timer \
    --name trigger-for-postgresql \
    --invoke-function-name function-for-postgresql \
    --invoke-function-service-account-id $SERVICE_ACCOUNT_ID \
    --cron-expression '* * * * ? *'   

Cron-выражение * * * * ? * означает вызов функции `function-for-postgresql` один раз в минуту. Подробнее про Cron-выражения можно прочитать в [документации](https://cloud.yandex.ru/docs/functions/concepts/trigger/timer#cron-expression).  Успешное выполнение функции раз в минуту будет создавать запись в базе данных в чем вы можете убедиться просмотрев записи в таблице. Убедились? Поздравляем: вы успешно создали функцию, которая через заданный промежуток времени выполняется по триггеру, чтобы проверить доступность yandex.ru и записать результат проверки в базу данных.

# Удаление Триггера-таймера

По завершении лабораторной работы не забудьте удалить, созданный нами триггер `trigger-for-postgresql` иначе он будет работать и работать:

    yc serverless trigger delete trigger-for-postgresql
