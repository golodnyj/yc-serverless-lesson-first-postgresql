# Подключение к управляемым БД из функции
## Создание подключения

В консоли управления перейдите в рабочий каталог, в котором хотите создать подключение. Откройте сервис Cloud Functions.
В боковом меню перейдите на вкладку `Подключения к БД`. Нажмите кнопку `Создать подключение`.

1. Введите имя, описание подключения и в выпадающем списке выберете `PostgreSQL`. 
2. Укажите кластер — `my-pg-database`
3. Укажите базу данных — `db1`
4. Введите данные пользователя БД имя  `user1` и пароль `user1user1`.
5. Нажмите кнопку `Создать`.

После успешного создания подключения в подробностях подключения скопируйте `идентификатор` и `точку входа`. Они будут использованы в функции на следующем шагу. 
