# Maxim Puhov, 153501
Как тема курса я выбрал "Интернет-магазин"

Сущности:
Пользователь - это челок, использующий магазин.
Товар - это продукт, который продается в интернет-магазине.
Категория - это группа товаров, связанных по общему признаку.
Заказ - это запрос клиента на покупку товаров.
Адрес - это место, куда доставляется заказ.
Способ оплаты - это способ оплаты заказа.
Статус заказа - это состояние заказа, например, "в обработке", "отправлен", "получен".
Комментарий - это комментарий к заказу, например, пожелания или жалобы.
Промоакция - это мероприятие, направленное на стимулирование продаж товаров.
Отзыв - это оценка товара, оставленная покупателем.

Дополнительные параметры для каждой сущности:

Товар:
-название
-описание
-цена
-изображение
-количество на складе

-Категория:
-название
-описание
-изображения

Заказ:
-дата создания
-дата оплаты
-дата доставки

Адрес:
-страна
-город
-улица
-номер дома
-индекс

Способ оплаты:
-название
-описание

Статус заказа:
-название
-описание

Комментарий:
-текст комментария

Промоакция:
-название
-описание
-дата начала
-дата окончания
-скидка

Отзыв:
-текст отзыва
-оценка
-дата публикации


В проекте "Интернет-магазин" можно выделить следующие роли:

Администратор:
-Может создавать, редактировать и удалять пользователей, роли и настройки системы.
-Может управлять каталогом товаров, категориями и поставщиками.
-Может отслеживать заказы и платежи.
-Может анализировать данные о продажах.

Продавец:
-Может выполнять все действия, доступные менеджеру, а также:
-Принимать и обрабатывать заказы.
-Отправлять товары покупателям.
-Обрабатывать возвраты и обмен товаров.

Покупатель:
-Может просматривать каталог товаров.
-Добавлять товары в корзину.
-Оформлять заказы.
-Отслеживать статус заказов.
-Отправлять отзывы о товарах.
