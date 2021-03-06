## finance.updateAccount: Изменение счета 

> Пример запроса:

```php
<?php
$url = 'https://joinposter.com/api/finance.updateAccount'
 . '?token=687409:4164553abf6a031302898da7800b59fb';

$account = [
    'account_id' => 3,
    'account_name' => 'Сейф',
    'currency_id' => 3,
    'type' => 1,
    'balance_start' => 0,
];

$data = sendRequest($url, 'post', $account);

```

> Пример ответа:

```json
{
  "response":4
}
```

Метод изменяет свойства счета 

### HTTP запрос

`POST https://joinposter.com/api/finance.updateAccount`

### POST-параметры запроса finance.updateAccount

Параметр | Описание
-------- | --------
account_id | id счета
account_name | Название счета
type | Тип счета: 1 — безналичный, 2 — банковская карта, 3 — наличные
balance_start | Остаток денег на счете на момент создания, в гривнах\рублях
currency_id | Id валюты в Poster: 1 — гривна, 2 — рубль, 3 — доллар, 4 — евро, 5 — тенге, 6 — лари, 7 — бат, 8 — armenia dram

### Параметры ответа finance.updateAccount

Параметр | Описание
-------- | --------
response | id измененного счета
