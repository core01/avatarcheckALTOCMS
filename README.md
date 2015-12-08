# Исправление удаленных аватарок ALTO CMS

## Первоначальные действия
- Сделать бэккап таблицы user, на всякий случай.
- Необходимо выполнить SQL запрос для придания аватаркам относительного пути:
- `UPDATE LS_user SET user_profile_avatar = REPLACE(user_profile_avatar, 'http://site.ru', '')`
- Замените `LS_` на Ваш префикс, а также имя и протокол для вашего сайта, в дальнейшем можно будет выполнить обратный запрос
- Если у Вас большое количество пользователей установите соответсвующее значение `max_execution_time` или `set_time_limit` в php.ini

### Выполнение скрипта
- Положить папку скрипта в каталог сайта с ALTO CMS
- Запустить скрипт по адресу http://site.ru/altoavatarcheck/avatarfix.php
- Ждать результатов выполнения скрипта
- Выполить запрос, который вернет имя вашего домена в путь аватарок `UPDATE LS_user SET user_profile_avatar = REPLACE(user_profile_avatar, '/uploads', 'http://site.ru/uploads')` [Пояснение](http://altocms.ru/1471.html#comment25086)

В моём случае было 2573 пользователя с аватарками, у 782 не существовали файлы аватарок.

После выполнения скрипта отобразится массив пользователей и их id у которых изменены значения аватарок.