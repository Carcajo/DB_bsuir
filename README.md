# Maxim Puhov, 153501
https://drawsql.app/teams/carcajo/diagrams/lab-db
Как тема курса я выбрал "Интернет-магазин"

Сущности:
<ul>
<li>Пользователь - это человек, использующий магазин.</li>
<li>Роли - разный уровень доступа и возможностей</li>
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

Пользователь:
<ul>
<li>id BIGSERIAL PRIMARY KEY NOT NULL</li>
<li>first_name VARCHAR(50) NOT NULL</li>
<li>last_name VARCHAR(50) NOT NULL </li>
<li>email VARCHAR(50) ~ '.@.+..' NOT NULL</li>
<li>FOREIGN KEY order_id REFERENCES order(id) NOT NULL</li>
<li>FOREIGN KEY product_id REFERENCES product(id) NOT NULL</li>
</ul>

Товар:
<ul>
<li>id BIGSERIAL PRIMARY KEY NOT NULL</li>
<li>name VARCHAR(50) NOT NULL</li>
<li>description VARCHAR(200) NOT NULL </li>
<li>description DECIMAL(8,2) NOT NULL</li>
<li>photo BLOB NOT NULL</li>
<li>availability INT NOT NULL</li>
<li>FOREIGN KEY category_id REFERENCES category(id) NOT NULL</li>
</ul>

-Категория:
<ul>
<li>id BIGSERIAL PRIMARY KEY NOT NULL</li>
<li>name VARCHAR(50) NOT NULL</li>
<li>description VARCHAR(200) NOT NULL</li>
</ul>

Заказ:
<ul>
<li>id BIGSERIAL PRIMARY KEY NOT NULL</li>
<li>date_of_create DATE NOT NULL</li>
<li>date_of_payment DATE NOT NULL</li>
<li>date_of_delivery DATE NOT NULL</li>
<li>product_id BIGINT NOT NULL</li>
<li>FOREIGN KEY feedback  _id REFERENCES feedback(id) NOT NULL</li>
<li>FOREIGN KEY product_id REFERENCES product(id) NOT NULL</li>
<li>FOREIGN KEY address_id REFERENCES address(id) NOT NULL</li>
</ul>

Адрес:
<ul>
<li>id SERIAL PRIMARY KEY NOT NULL</li>
<li>country VARCHAR(50) NOT NULL</li>
<li>city VARCHAR(50) NOT NULL</li>
<li>street VARCHAR(50) NOT NULL</li>
<li>house_number VARCHAR(3) NOT NULL</li>
<li>index VARCHAR(10) NOT NULL</li>
<li>FOREIGN KEY user_id REFERENCES user(id) NOT NULL</li>
</ul>

Способ оплаты:
<ul>
<li>id SERIAL PRIMARY KEY NOT NULL</li>
<li>name VARCHAR(50) NOT NULL</li>
<li>FOREIGN KEY user_id REFERENCES user(id) NOT NULL</li>
</ul>

Статус заказа:
<ul>
<li>id SERIAL PRIMARY KEY NOT NULL</li>
<li>name VARCHAR(50) NOT NULL</li>
<li>description VARCHAR(200) NOT NULL</li>
<li>FOREIGN KEY order_id REFERENCES order(id) NOT NULL</li>
</ul>

Промоакция:
<ul>
<li>id BIGSERIAL PRIMARY KEY NOT NULL</li>
<li>name VARCHAR(50) NOT NULL</li>
<li>description VARCHAR(200) NOT NULL</li>
<li>date_of_start DATE NOT NULL</li>
<li>date_of_finish DATE NOT NULL</li>
<li>discount INT NOT NULL</li>
<li>FOREIGN KEY user_id REFERENCES user(id) NOT NULL</li>
<li>FOREIGN KEY product_id REFERENCES product(id) NOT NULL</li>
</ul>

Отзыв:
<ul>
<li>id SERIAL PRIMARY KEY NOT NULL</li>
<li>text отзыва VARCHAR(300) NOT NULL</li>
<li>mark INT NOT NULL</li>
<li>FOREIGN KEY user_id REFERENCES user(id) NOT NULL</li>
</ul>

Корзина:
<ul>
<li>id BIGSERIAL PRIMARY KEY NOT NULL</li>
<li>total_cost DECIMAL(8,2) NOT NULL</li>
<li>number_of_products INT NOT NULL</li>
<li>discount_on_the_total_cost INT NOT NULL</li>
<li>finaly_cost DECIMAL(8,2) NOT NULL</li>
<li>FOREIGN KEY order_id REFERENCES order(id) NOT NULL</li>
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
</ul>

Покупатель:
<ul>
<li>Может просматривать каталог товаров.</li>
<li>Добавлять товары в корзину.</li>
<li>Оформлять заказы.</li>
<li>Отслеживать статус заказов.</li>
<li>Отправлять отзывы о товарах.</li>
</ul>

Неавторизованный пользователь:
<ul>
<li>Может просматривать каталог товаров</li>
</ul>


![image](https://github.com/Carcajo/DB_bsuir/assets/93794796/258bd2fd-a125-4217-8027-e2a4287f7c21)

