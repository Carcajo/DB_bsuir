# Maxim Puhov, 153501, Сайт Продажи вещей.

Функциональные требование:
<ul>
  <li></li>
</ul>

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

ЭЭЭЭЭЭ

# 2. Функциональные требования:
  1. Авторизация пользователя.
  2. Управление пользователями (CRUD).
  3. Ролевая система(Клиент, Сотрудник, Админ).
  4. Ведение журнала действий пользователя.(Покупки, Отзывы)
  6. Просмотр сортудников(Клиент)
  7. Управление Фруктами, Производитлями (Сотрудник).
  8. Управление отзывами CRUD (Админ).
     
# 3. Список таблиц для базы данных:
  1. "Фрукты":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Название (VARCHAR(50), NN)
        Дата изготовления (DATETIME, NN)
        Цена (INT, NN)
        Срок годности(INT, NN)
        ID производителя(FOREIGN KEY REFERENCES Производители(ID), NN)
    Связи:  
       Связь с таблицей "Производители" в отношении "Многие к одному" (Many-to-One) через поле ID производителя.

  2. "Заказы":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Дата создания (DATETIME, NN)
        Сумма заказа (INT, NN)
        Количество товара(INT, NN)
        ID клиента (INT, FOREIGN KEY REFERENCES Клиенты(ID), NN)
        ID фрукта (INT, FOREIGN KEY REFERENCES Фрукты(ID), NN)
        
    Связи:
       Связь с таблицей "Клиенты" в отношении "Многие к одному" (Many-to-One) через поле ID клиента.
       Связь с таблицей "Фрукты" в отношении "Многие к одному" (Many-to-One) через поле ID фрукта.

  3. "Клиенты":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Адрес (VARCHAR(200), NN) 
        ID пользователя (INT, UNIQUE, NN)
   Связи:
       Связь с таблицей "Пользователи" в отношении "Один к одному" (One-to-One) через поле ID клиента.

  4. "Роли":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Название роли (VARCHAR(25), UNIQUE, NN)

  5. "Отзывы":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Текст отзыва (TEXT, NN)
        Оценка (INT, NN)
        ID фрукта (INT, FOREIGN KEY REFERENCES Фрукты(ID), NN)
        ID клиента (INT, FOREIGN KEY REFERENCES Клиенты(ID), NN)
    Связи:
        Связь с таблицей "Фрукты" в отношении "Многие к одному" (Many-to-One) через поле ID автомобиля.
        Связь с таблицей "Клиенты" в отношении "Многие к одному" (Many-to-One) через поле ID клиента.

  6. "Сотрудники":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Зарплата (INT, NN)
        ID пользователя (INT, UNIQUE, NN)
        
        ID времени (INT, FOREIGN KEY REFERENCES Рабочее время сотрудников(ID))
    Связи:
        Связь с таблицей "Рабочее время сотрудников" в отношении "Многие к одному" (Many-to-One) через поле ID времени.
       Связь с таблицей "Пользователи" в отношении "Один к одному" (One-to-One) через поле ID клиента.
       
  7. "Рабочее время сотрудников":
    
    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Дата и время начала работы (DATETIME, NN)
        Дата и время окончания работы (DATETIME, NN)
        
  8. "Доставка":
      
    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        ID заказа (INT, UNIQUE, NN)
        Дата доставки (DATETIME, NN)
    Связи:
        Связь с таблицей "Заказы" в отношении "Один к одному" (One-to-One) через поле ID заказа.
      
  9. "Производители":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Страна производителя (VARCHAR(50), NN)
        Имя комании (VARCHAR(50), NN)
        
 10. "Пользователи":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Имя ((VARCHAR(50), NN)
        Фамилия ((VARCHAR(50), NN)
        Телефон (CHAR(13) ~ '+375[0-9]{9}' NN,)
        Пароль ((VARCHAR(50), NN)
        ID Роли (INT, FOREIGN KEY REFERENCES Роли(ID))
    Связи:
        Связь с таблицей "Роли" в отношении "Многие к одному" (Many-to-One) через поле ID Роли.

  11. "Должности":
    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Название(VARCHAR(50), NN)
      
  12. "Должности/Сотрудники"(вспомогательная):
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        ID должности(INT, FOREIGN KEY REFERENCES(Должности), NN)
        ID сотрудника(INT, FOREIGN KEY REFERENCES(Сотрудники), NN)
    Связи:
        Связь между Должности/Сотрудники(Many to many) через поля  ID должности и ID сотрудника
      
        

# 4. Use-case:
  Неавторизованный пользователь:
  
    Просматривать список сотрудников
    Просматривать каталог фруктов
    Просматривать отзывы
    Авторизовываться 
    
  Авторизованный пользователь(Клиент):
    
    Все, что и неавторизованный пользователь
    Совершать заказ
    Оставлять отзыв
    
  Сотрудник:
   
    Все, что и клиент
    CRUD к фруктам, Производителям
    
  Админ:
  
    Все, что и сотрудник
    CRUD ко всем моделям
    

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
<li>Может создавать, редактировать и удалять пользователей и настройки системы.</li>
<li>Может управлять каталогом товаров и их категориями</li>
<li>Может отслеживать покупки</li>
<li>Может анализировать данные о продажах.</li>
</ul>

Пользователь:
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

