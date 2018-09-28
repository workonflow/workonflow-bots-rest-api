# Contact requests

### contact/create

**Метод для создания контактов**

```js
  api.workonflow.com/{teamid}/contact/create/{body}
```

**Parameters:**

| field         | type          | description|
| ------------- |---------------| :---------------------- |
| basicData     | object        | Takes an object with the name of the contact |
| customFields  | array         | Field for adding channels to the contact, содержит в себе объекты содержащие не типичную информацию о пользователе |
| contactId     | string        | id of contact |
| label         | string        | nome of custom field   |
| value         | string        | value of custom field  |
| type          | string        | type of custom field   |

**Body message example:**

```json
{
  "basicData": {
    "name": "Alex",
    "email": "email@email.com"
  },
  "customFields": [
    {"id": "B1R5NTS3z", "label": "Company", "value": "", "type": "company"},
    {"id": "B1l094TB2M", "label": "Work phone", "value": "", "type": "phone"},
    {"id": "rkbA9VTH3M", "label": "Work e-mail", "value": "", "type": "email"}
  ]
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "basicData": {"name": "Alex", "email": "email@email.com"}, "customFields": [{"id": "B1R5NTS3z", "label": "Company", "value": "", "type": "company"}, {"id": "B1l094TB2M", "label": "Work phone", "value": "", "type": "phone"}, {"id": "rkbA9VTH3M", "label": "Work e-mail", "value": "", "type": "email"}] }' https://api.workonflow.com/333ccc134c0319001573485e/contact/create
```

**Response example:**

```js
  { code: 200, message: "OK", data: { contactId: '1491eh1029318du1dqw9' } }
```
---

## contact/local

**Метод для получения "языка" пользователя**

```js
  api.workonflow.com/{teamid}/contact/local/{body}
```

**Parameters:**

| field         | type          | description|
| ------------- |---------------| ----------------------:|
| userId     | string        | id of user |

**Body message example:**
```json
{
  "userId":"5b0525134c0319001573485e"
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "userId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/contact/create
```

**Response example:**

```js
  { code: 200, message: "OK", data: { userId: "5b0525134c0319001573485e", local: "us" } }
```
---
## contact/get

**Метод для получения пользоватей**
```js
  api.workonflow.com/{teamid}/contact/get/{body}
```

**Parameters:**

| field         | type    | description|
| ------------- |---------| ----------------------:|
| userId        | string  | Contact or user ID     |
| userIds       | array   | Several contact or user IDs|
| billingType   | string  | тип пользователя, может быть users, contact или bots |
| basicData     | object  | содержит в себе имя, телефоны и почтовые адреса контакта |
| extension     | string  | внутренний номер сотрудника |
| teamId        | string  | id of team |
| createdAt     | string  | дата создания в формате ISO, пример: '2018-04-02T13:51:03.800Z' |
| updatedAt     | number  | дата последнего обновления в формате timestamp, пример: 1517574060991|
| color         | string  | цвет фона и иконки пользователя в виде '#ffffff' |
| status        | string  | статус пользователя онлайн или нет |
| voiceRules    | array   | настройки голосовых каналов у пользователя |

**Body message example:**

```json
{
  "userId":"5b0525134c0319001573485e",
  "userIds":["5afd6d369a88ff00190baf79", "5afd6d369a88ff22190baf79"]
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "userId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/contact/get
```
**Response example:**

```js
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
