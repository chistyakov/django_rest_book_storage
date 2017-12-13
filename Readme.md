# Task from job interview
Сделать api для книжного магазина.

Кейсы, которые должны обрабатываться:
1. При загрузке приложения неавторизованным пользователем приложение
запрашивает список популярных книг. Метод вызывается часто, должна быть
оптимизация по скорости отдачи. Обновление топа книг происходит один раз в
сутки по расписанию.
2. Поиск и фильтрация книг по полям – название, имя и фамилия автора.
3. Покупка книги – привязка купленной книги к аккаунту пользователя.
4. Загрузка книги пользователем – необходимо проверять, что пользователь купил
книгу.

Модели предметной области:

1. Автор
   * Имя
   * Фамилия
   * Фото
2. Книга
   * Авторы (один или несколько)
   * Фото обложки (опционально)
   * Название
   * Описание (форматированный текст)
   * Цена
3. Пользователь
   * Имя
   * Телефон
   * Купленные книги
   * Идентификатор привязанной карты – один или несколько

Методы api:
1. Получить список книг (с фильтрацией по автору) – возвращает название книги,
фото обложки, имя, фамилию автора. В случае, если пользователь авторизован,
добавить отметку о покупке книги.
2. Получить информацию о книге – вся информация о книге и авторах. Если
пользователь авторизован и книгу куплена – ссылка для загрузки книги.
3. Купить книгу – добавляет книгу в список купленных – доступно только для
авторизованных пользователей.
4. Показать список купленных пользователем книг – доступно только для
авторизованных пользователей.
5. Получить топ книг.

Вся информация загружается через стандартную админку Django.

Покрыть любой кейс тестами.

Общение с платежной системой реализовать с помощью моков. API платежной системы
содержит один метод:
1. списать_деньги(идентификатор карты, сумма), возвращает bool – удалось ли
списать заданную сумму.

Стек технологий:
* Python 3.4+
* Django
* DRF
* Unit-tests + Django tests

Результат должен быть доступен в виде репозитория на github или bitbucket, система
контроля версий – git.

## How to run
```shell
docker build . -t bookstore
docker run -d -p 8000:8000 --name bookstore bookstore
Ctrl+C
```
