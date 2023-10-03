# Maxim Puhov, 153501, Сайт Продажи мужских цепочек определённого вида.

# 1. Функциональные требования:
  1. Авторизация пользователя.
  2. Управление пользователями (CRUD).
  3. Ролевая система(Клиент, Сотрудник, Админ).
  4. Ведение журнала действий пользователя.(Покупки, Отзывы)
  6. Просмотр сортудников(Клиент)
  7. Управление Товароми, Производитлями (Сотрудник).
  8. Управление отзывами CRUD (Админ).
     
# 2. Список таблиц для базы данных:
  1. "Цепи":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Название (VARCHAR(50), NN)
        Цена (INT, NN)
        Материал(VARCHAR(50), NN)
        ID производителя(FOREIGN KEY REFERENCES Производители(ID), NN)
        фото (BLOB, NN)
    Связи:  
       Связь с таблицей "Производители" в отношении "Многие к одному" (Many-to-One) через поле ID производителя.

  2. "Заказы":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Дата создания (DATETIME, NN)
        Количество товара(INT, NN)
        ID клиента (INT, FOREIGN KEY REFERENCES Клиенты(ID), NN)
        
    Связи:
       Связь с таблицей "Клиенты" в отношении "Многие к одному" (Many-to-One) через поле ID клиента.

  3. "Роли":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Название роли (VARCHAR(25), UNIQUE, NN)

  4. "Отзывы":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Текст отзыва (TEXT, NN)
        Оценка (INT, NN)
        ID цепи (INT, FOREIGN KEY REFERENCES Цепи(ID), NN)
        ID клиента (INT, FOREIGN KEY REFERENCES Клиенты(ID), NN)
    Связи:
        Связь с таблицей "Цепи" в отношении "Многие к одному" (Many-to-One) через поле ID цепи.
        Связь с таблицей "Клиенты" в отношении "Многие к одному" (Many-to-One) через поле ID клиента.      
      
  5. "Производители":

    Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Страна производителя (VARCHAR(50), NN)
        Имя комании (VARCHAR(50), NN)
        
  6. "Пользователи":

    Поля:
      ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
      Имя ((VARCHAR(50), NN)
      Фамилия ((VARCHAR(50), NN)
      email(VARCHAR(100) ~ '.*@.+\..*')
      ID Роли (INT, FOREIGN KEY REFERENCES Роли(ID))
    Связи:
      Связь с таблицей "Роли" в отношении "Многие к одному" (Many-to-One) через поле ID Роли.

   7. "Адрес":

    Поля:
      ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
      Город ((VARCHAR(50), NN)
      Улица ((VARCHAR(50), NN)
      Номер дома ((VARCHAR(3), NN)
      Индекс ((VARCHAR(6), NN)
      ID пользователь (INT, FOREIGN KEY REFERENCES Пользователь(ID))
    Связи:
      Связь с таблицей "Пользователь" в отношении "Многие к одному" (Many-to-One) через поле ID пользователя.

   8. "Статус заказа":
    
     Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        статус(VARCHAR(50), NN)

   9. "Корзина":
    
     Поля:
        ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
        Общая стоимость (DECIMAL(8,2), NN)
        Количество товара (INT, NN)
        ID цепи (INT, FOREIGN KEY REFERENCES цепь(ID))
        ID заказа (INT, FOREIGN KEY REFERENCES заказ(ID))
     Связи:
        Связь с таблицей "Цепи" в отношении "Один ко многим" (Many-to-One) через поле ID цепи.
        Связь с таблицей "Заказ" в отношении "Один ко многим" (Many-to-One) через поле ID заказа.

  10."Доставка":
  
    Поля:
      ID (INT, PRIMARY KEY, AUTOINCREMENT, NN)
      ID заказа (INT, UNIQUE, NN)
      Дата доставки (DATETIME, NN)
    Связи:
      Связь с таблицей "Заказы" в отношении "Один к одному" (One-to-One) через поле ID заказа.
              

# 3. Use-case:
  Неавторизованный пользователь:
  
    Просматривать список сотрудников
    Просматривать каталог товара
    Просматривать отзывы
    Авторизовываться 
    
  Авторизованный пользователь(Клиент):
    
    Все, что и неавторизованный пользователь
    Совершать заказ
    Оставлять отзыв
    
  Админ:
  
    Все, что и сотрудник
    CRUD ко всем моделям


![image](https://github.com/Carcajo/DB_bsuir/assets/93794796/930af3d1-98d2-4666-9074-0b06e1265e65)



