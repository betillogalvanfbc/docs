## access.getEmployees: Список сотрудников

> Пример запроса:

```php
<?php
$url = 'https://joinposter.com/api/access.getEmployees'
 . '?token=687409:4164553abf6a031302898da7800b59fb';

$data = sendRequest($url);
```

> Пример ответа:

```json
{
  "response":[
    {
      "user_id":3,
      "name":"Семён Суханов",
      "role_id": 4,
      "role_name": "Официант",
      "access_mask": 1,
      "last_in":"2017-03-07 13:03:47"
    },
    {
      "user_id":9,
      "name":"Дарья Кошелева",
      "user_type":0,
      "role_id": 3,
      "role_name": "Администратор зала",
      "access_mask": 257,
      "last_in":"2017-03-07 14:03:03"
    },
    {
      "user_id":10,
      "name":"Вячеслав Максимочкин",
      "role_id": 2,
      "role_name": "Маркетолог",
      "access_mask": 34,
      "last_in":"2017-03-07 10:03:06"
    }
  ]
}
```

Метод возвращает список сотрудников

### HTTP GET запрос

`https://joinposter.com/api/access.getEmployees`

### Параметры ответа access.getEmployees

Параметр | Описание
-------- | --------
response | Массив объектов

Внутри параметра `response` лежит массив, в каждом элементе которого есть следующие параметры:

Параметр | Описание
-------- | --------
user_id | Id сотрудника
name | Имя и фамилия сотрудника
role_id | Id должности сотрудника
role_name | Название должности
access_mask | [Битовая маска доступа](https://ru.wikipedia.org/wiki/%D0%91%D0%B8%D1%82%D0%BE%D0%B2%D0%B0%D1%8F_%D0%BC%D0%B0%D1%81%D0%BA%D0%B0) в которой каждый бит отвечает за доступ к определенному разделу Poster. Расшифровка значений всех битов приведена в таблице ниже.  
user_type | Должность сотрудника: 0 — официант, 1 — администратор, 2 — маркетолог, 3 — кладовщик, 4 — администратор зала, 50 — менеджер, 90 — владелец 
last_in | Дата последнего входа в админ-панель
inn | ИНН сотрудника, который будут передан на фискальный регистратор. Отображается только для клиентов из России с включенной фискализацией.
name_for_fiscal | Полное имя и фамилия сотрудника, которые будут переданы на фискальный регистратор. Отображаются только для клиентов из России с включенной фискализацией.


Все сотрудники имеют должность и права доступа. По умолчанию в Poster есть следующие должности:

* Официант — нет доступа в админ-панель
* Администратор зала — администрирование заказов на терминале
* Маркетолог — доступ к статистике и маркетинговым инструментам
* Кладовщик — доступ к складам и поставкам


Но пользователь может модифицировать эти должности. 
Поэтому, чтобы проверить к каким раздела каждый сотрудник имеет доступ используйте побитовое «И» (&) для поля `access_mask` и следующих битов:


Бит | Раздел Poster
--- | -------------
1 | Терминал
2 | Статистика
4 | Финансы
8 | Меню
16 | Склад
32 | Маркетинг
64 | Доступ
128 | Настройки
256 | Администратор зала
512 | Настройки безопасности
