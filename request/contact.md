# Contact requests

## Метод для создания контактов
Метод позволяет создавать внешних юзеров, которых можно прикрепить к треду, и общаться с ними посредством почты или телефонии

```https://botapi.workonflow.com/{teamid}/contact/create/{body}```

### Параметры:

| field         | type          | description| required |
| ------------- |---------------| ----------------------|----:|
| basicData     | object        | принимает объект с одним обязательным полем **name** - имя пользователя | yes
| customFields  | array of objects  | Массив объектов, содержащих дополнительную информацию о пользователе, такую как: рабочий/домашний телефон, скайп, эл. почта и пр. |

|Пример объекта для customFields |  type | description | required|
|-----|----:|-----:|---:|
| label         | string        | имя кастомного поля   | yes |
| value         | string        | значение кастомного поля  | yes |
| type          | string        | тип кастомного поля (email, phone)   | yes |
| id            | string        | уникальные идентификатор кастомного поля | yes |

### Пример тела запроса:

```json
{
  "basicData": {
    "name": "Alex"
  },
  "customFields": [
    {"id": "B1R5NTS3z", "label": "Company", "value": "OOO TS", "type": "company"},
    {"id": "B1l094TB2M", "label": "Work phone", "value": "777", "type": "phone"},
    {"id": "rkbA9VTH3M", "label": "Work e-mail", "value": "work@work.com", "type": "email"}
  ]
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "basicData": {"name": "Alex", "email": "email@email.com"}, "customFields": [{"id": "B1R5NTS3z", "label": "Company", "value": "OOO TS", "type": "company"}, {"id": "B1l094TB2M", "label": "Work phone", "value": "777", "type": "phone"}, {"id": "rkbA9VTH3M", "label": "Work e-mail", "value": "work@work.com", "type": "email"}] }' https://botapi.workonflow.com/333ccc134c0319001573485e/contact/create```

### Пример ответа:
```json
  {
    "code": 200,
    "message": "OK",
    "data": { "contactId": "1491eh1029318du1dqw9" } }
```
---

## Метод для получения "языка" пользователя

```https://botapi.workonflow.com/{teamid}/contact/local/{body}```

### Параметры:

| field         | type          | description| required |
| ------------- |---------------| ----------------------:| ----:|
| userId     | string        | идентификатор юзера | yes |

### Пример тела запроса:
```json
{
  "userId":"5b0525134c0319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "userId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/contact/create```

### Пример ответа:

```json
  {
    "code": 200,
    "message": "OK",
    "data": { "userId": "5b0525134c0319001573485e", "local": "us" }
  }
```
---

## Метод для получения пользоватей
Метод позволяет получить всех пользователей, находящихся в тиме.

```https://botapi.workonflow.com/{teamid}/contact/read/{body}```

### Параметры:
> **Внимание!** Одно из полей обязательно должно быть передано в запросе: userId, userIds, customField

| field         | type    | description|
| ------------- |---------| ----------------------:|
| userId        | string  | индетификатор юзера     |
| userIds       | array   | массив идентификаторов юзеров|
| billingType   | string  | тип юзера: users, contacts or bots |
| customField   | string  | кастомное поля юзера (почта, телефон и т.п.)

### Пример тела запроса:

```json
{
  "billingType": "users"
}
```

### Пример запроса с помощью curl:

```curl -H "Content-Type: application/json" -X POST -d '{ "billingType" : "users" }' https://botapi.workonflow.com/333ccc134c0319001573485e/contact/read```

### Пример ответа:
```json
{
  code: 200,
  message: 'OK',
  data: [ {
    billingType: 'users',
    basicData: {
      name: 'user name',
      email: [ 'user email' ],
      phone: [ 'user phone' ]
    },
    extension: 'number extension in system',
    teamId: 'team id',
    createdAt: '2017-10-30T10:15:53.245Z',
    updatedAt: 1517574060991,
    color: '#ffffff',
    status: 'off',
    voiceRules: [ {
      type: 'webrtc',
      enabled: true,
      timeout: '',
      extension: '100*9 (default number extension + *9)',
      visible: true
    }, {
      type: 'sip',
      enabled: true,
      timeout: '',
      extension: '100*1 (default number extenseion + *1)',
      visible: true
    } ]
  } ]
}
```
