# Заказы международного продуктового онлайн магазина.

В качестве исходных данных выступает файл orders.txt, представляющий собой список заказов. Файл состоит из набора строк с колонками, разделенных между собой точкой с запятой. \
Каждая строка содержит информацию о заказе продуктов в формате:

    <Номер заказа>;<Набор прродуктов>;<ФИО заказчика>;<Адрес доставки>;<Номер телефона>;<Приоритет доставки>
---
#### Каждая колонка о заказе имеет свой форматно-логический контроль:
- ___Номер заказа___ - пятизначное число. Поле не может быть пустым. Поле всегда заполненное.
- ___Набор продуктов___ - перечисление наименований через запятую с пробелом (могут повторяться). Поле не может быть пустым. Поле всегда заполненное.
- ___ФИО заказчика___ - в формате: **_<Фамилия> <Имя> <Отчество>_**. Поле всегда заполняется. Поле может не иметь отчества (_не является ошибкой_).
- ___Адрес доставки___ - адрес состоящий из шаблона: ___<Страна>. <Регион>. <Город>. <Улица>___. Например: (Российская Федерация. Москва. Москва. Новокузнецкая). Поле может быть пустым (_является ошибкой_).
- ___Номер телефона___ - по шаблону: **+x-xxx-xxx-xx-xx**, где x - любая цифра 0-9. Поле может быть пустым (_является ошибкой_). Поле может быть заполнено не по шаблону (_является ошибкой_).
- ___Приоритет доставки___ - перечисление **MAX, MIDDLE, LOW**. Поле не может быть пустым. Поле всегда заполнено.

---
   
#### Необходимо прочитать данные из файла, провалидировать все заказы на предмет ошибок:
1. Ошибка заполнения адреса доставки
2. Ошибка заполнения номера телефона

Заказы с ошибкой необходимо сохранить в файл **_non_valid_orders.txt_** в формате:

    <Номер заказа>;<Тип ошибки> (1 или 2);<Значение атрибута заказа, в котором содержится ошибка (или текстовое сообщение "no data")>
P.S. Если ошибок в одном заказе несколько, то сохранить в файл несколько ошибок по одному заказу.

Все провалидированные заказы необходимо **отсортировать** по Стране из адреса заказа, а так же **отсортировать** по Приоритету доставки (**_от MAX до LOW_**) и сохранить в файлы заказов по странам:

order_country1.txt\
order_country2.txt\
...

Формат сохранения:

    <Номер заказа>;<Набор продуктов (в формате: 'Бананы x4, Гречка x2, Сметана, Яблоко x6, Масло, Пельмени, Сыр x2)>;<ФИО заказчика>;<Адрес доставки (в формате: Регион. Город. Улица)>;<Номер телефона>;<Приоритет доставки>

---
    
### Пример входных данных

    31987;Сыр, Колбаса, Сыр, Макароны, Колбаса;Петрова Анна;Россия. Ленинградская область. Санкт-Петербург. набережная реки Фонтанки;+7-921-456-78-90;MIDDLE
    87459;Молоко, Яблоки, Хлеб, Яблоки, Молоко;Иванов Иван Иванович;Россия. Московская область. Москва. улица Пушкина;+7-912-345-67-89;MAX
    31987;Сыр, Колбаса, Макароны, Сыр, Колбаса;Петрова Анна Сергеевна;Франция. Иль-де-Франс. Париж. Шанз-Элизе;+3-214-020-50-50;MIDDLE
    56342;Хлеб, Молоко, Хлеб, Молоко;Смирнова Мария Леонидовна;Германия. Бавария. Мюнхен. Мариенплац;+4-989-234-56;LOW                                              (невалидный номер телефона)
    48276;Яблоки, Макароны, Яблоки;Алексеев Алексей Алексеевич;Италия. Лацио. Рим. Колизей;+3-061-234-56-78;MAX
    65829;Сок, Вода, Сок, Вода;Белова Екатерина Михайловна;Испания. Каталония. Барселона. Рамбла;+34-93-1234-567;LOW                                                (невалидный номер телефона)
    72901;Чай, Кофе, Чай, Кофе;Михайлов Сергей Петрович;Великобритания. Англия. Лондон. Бейкер-стрит;+4-207-946-09-58;LOW
    84756;Печенье, Сыр, Печенье, Сыр;Васильева Анна Владимировна;Япония. Шибуя. Шибуя-кроссинг;+8-131-234-5678;MAX                                                  (невалидный адрес доставки и номер телефона)
    90385;Макароны, Сыр, Макароны, Сыр;Николаев Николай;;+1-416-123-45-67;LOW                                                                                       (невалидный адрес доставки)

В итоге должны быть созданы файлы:

    order_Россия.txt
    order_Франция.txt
    order_Италия.txt
    order_Великобритания.txt
    non_valid_orders.txt

Содержимое order_Россия.txt:

    87459;Молоко x2, Яблоки x2, Хлеб;Иванов Иван Иванович;Московская область. Москва. улица Пушкина;+7-912-345-67-89;MAX
    31987;Сыр x2, Колбаса x2, Макароны;Петрова Анна;Ленинградская область. Санкт-Петербург. набережная реки Фонтанки;+7-921-456-78-90;MIDDLE

Содержимое order_Франция.txt:

    31987;Сыр x2, Колбаса x2, Макароны;Петрова Анна Сергеевна;Иль-де-Франс. Париж. Шанз-Элизе;+3-214-020-50-50;MIDDLE

Содержимое order_Италия.txt:

    48276;Яблоки x2, Макароны;Алексеев Алексей Алексеевич;Лацио. Рим. Колизей;+3-061-234-56-78;MAX

Содержимое order_Великобритания.txt:

    72901;Чай x2, Кофе x2;Михайлов Сергей Петрович;Англия. Лондон. Бейкер-стрит;+4-207-946-09-58;LOW

Содержимое non_valid_orders.txt:

    56342;2;+4-989-234-56
    65829;2;+34-93-1234-567
    84756;2;+8-131-234-5678
    84756;1;Япония. Шибуя. Шибуя-кроссинг
    90385;1;no data







