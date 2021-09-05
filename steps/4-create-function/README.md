# Создание Функции

Для того чтобы создать функцию прежде всего определим переменные для инициации подключения: `CONNECTION_ID`, `DB_USER`, `DB_HOST` с помощью следующих команд:

    echo "export CONNECTION_ID=<CONNECTION_ID>" >> ~/.bashrc && . ~/.bashrc
    echo "export DB_USER=<DB_USER>" >> ~/.bashrc && . ~/.bashrc
    echo "export DB_HOST=<DB_HOST>" >> ~/.bashrc && . ~/.bashrc

    echo "export CONNECTION_ID=akfk8b507ja0pl0riq66" >> ~/.bashrc && . ~/.bashrc
    echo "export DB_USER=user1" >> ~/.bashrc && . ~/.bashrc
    echo "export DB_HOST=akfk8b507ja0pl0riq66.postgresql-proxy.serverless.yandexcloud.net" >> ~/.bashrc && . ~/.bashrc

Они будут использованы в функции function-for-postgresql.py. 

Создадим нашу функцию `function-for-postgresql`, при этом сразу зададим все необходимые переменные и сервисный аккаунт:

    yc serverless function create \
    --name  function-for-postgresql \
    --description "function for postgresql"

    yc serverless function version create \
    --function-name=function-for-postgresql \
    --memory=256m \
    --execution-timeout=5s \
    --runtime=python37 \
    --entrypoint=function-for-postgresql.entry \
    --service-account-id $SERVICE_ACCOUNT_ID \
    --environment VERBOSE_LOG=True \
    --environment CONNECTION_ID=$CONNECTION_ID \
    --environment DB_USER=$DB_USER \
    --environment DB_HOST=$DB_HOST \
    --source-path function-for-postgresql.py

Проверим работоспособность функции: 

    yc serverless function version list --function-name function-for-postgresql
    yc serverless function invoke --name function-for-postgresql

Успешное вызов функции приводит к измерению времени ответа сайта и формировании записи в базе данных.  