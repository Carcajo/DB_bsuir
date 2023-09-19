# Maxim Puhov, 153501
https://drawsql.app/teams/carcajo/diagrams/lab-db
Как тема курса я выбрал "Интернет-магазин"

Сущности:
<ul>
<li>Пользователь - это челок, использующий магазин.</li>
<li>Товар - это продукт, который продается в интернет-магазине.</li>
<li>Категория - это группа товаров, связанных по общему признаку.</li>
<li>Заказ - это запрос клиента на покупку товаров.</li>
<li>Адрес - это место, куда доставляется заказ.</li>
<li>Способ оплаты - это способ оплаты заказа.</li>
<li>Статус заказа - это состояние заказа, например, "в обработке", "отправлен", "получен".</li>
<li>Комментарий - это комментарий к заказу, например, пожелания или жалобы.</li>
<li>Промоакция - это мероприятие, направленное на стимулирование продаж товаров.</li>
<li>Отзыв - это оценка товара, оставленная покупателем.</li>
<li>Корзина - это место, где сохраняются выбранные товары</li>
</ul>

Дополнительные параметры для каждой сущности:

Товар:
<ul>
<li>название</li>
<li>описание</li>
<li>цена</li>
<li>изображение</li>
<li>количество на складе</li>
</ul>

-Категория:
<ul>
<li>название</li>
<li>описание</li>
<li>изображения</li>
</ul>

Заказ:
<ul>
<li>дата создания</li>
<li>дата оплаты</li>
<li>дата доставки</li>
</ul>

Адрес:
<ul>
<li>страна</li>
<li>город</li>
<li>улица</li>
<li>номер дома</li>
<li>индекс</li>
</ul>

Способ оплаты:
<ul>
<li>название</li>
<li>описание</li>
</ul>

Статус заказа:
<ul>
<li>название</li>
<li>описание</li>
</ul>

Комментарий:
<ul>
<li>текст комментария</li>
</ul>

Промоакция:
<ul>
<li>название</li>
<li>описание</li>
<li>дата начала</li>
<li>дата окончания</li>
<li>скидка</li>
</ul>

Отзыв:
<ul>
<li>текст отзыва</li>
<li>оценка</li>
<li>дата публикации</li>
</ul>

В проекте "Интернет-магазин" можно выделить следующие роли:

Администратор:
<ul>
<li>Может создавать, редактировать и удалять пользователей, роли и настройки системы.</li>
<li>Может управлять каталогом товаров, категориями и поставщиками.</li>
<li>Может отслеживать заказы и платежи.</li>
<li>Может анализировать данные о продажах.</li>
</ul>

Продавец:
<ul>
<li>Принимать и обрабатывать заказы.</li>
<li>Отправлять товары покупателям.</li>
<li>Обрабатывать возвраты и обмен товаров.</li>
<li>Создавать и редактировать заказы.</li>
<li>Отслеживать статус заказов.</li>
<li>Обрабатывать возвраты и обмен товаров.</li>
</ul>

Покупатель:
<ul>
<li>Может просматривать каталог товаров.</li>
<li>Добавлять товары в корзину.</li>
<li>Оформлять заказы.</li>
<li>Отслеживать статус заказов.</li>
<li>Отправлять отзывы о товарах.</li>
</ul>
