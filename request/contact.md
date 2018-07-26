# Contact actions

### contact/create

**Метод для создания контактов**

```js
  api.workonflow.com/{teamid}/contact/create/{query}
```

**Parameters:**

| field         | type          | description|
| ------------- |---------------| ----------------------:|
| basicData     | object        | Takes an object with the name of the contact |
| customFields  | array         | Field for adding channels to the contact  |
| contactId     | string        | id of contact |

**Query params example:**

```json
{
  "query": {
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
}
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"basicData": {"name": "Alex", "email": "email@email.com"}, "customFields": [{"id": "B1R5NTS3z", "label": "Company", "value": "", "type": "company"}, {"id": "B1l094TB2M", "label": "Work phone", "value": "", "type": "phone"}, {"id": "rkbA9VTH3M", "label": "Work e-mail", "value": "", "type": "email"}]}}' https://api.workonflow.com/333ccc134c0319001573485e/contact/create
```

**Response example:**

```js
  { code: 200, message: "OK", data: { contactId: '1491eh1029318du1dqw9' } }
```
---

## contact/local

**Метод для получения "языка" пользователя**

```js
  api.workonflow.com/{teamid}/contact/local/{query}
```

**Parameters:**

| field         | type          | description|
| ------------- |---------------| ----------------------:|
| userId     | string        | id of user |

**Query params example:**
```json
{
  "query":{
    "userId":"5b0525134c0319001573485e"
  }
}
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query":{"userId":"5b0525134c0319001573485e"}}' https://api.workonflow.com/333ccc134c0319001573485e/contact/create
```

**Response example:**

```js
  { code: 200, message: "OK", data: { userId: "5b0525134c0319001573485e", local: "us" } }
```
---
## contact/get

**Метод для получения пользоватей**
```js
  api.workonflow.com/{teamid}/contact/get/{query}
```

**Parameters:**
| field         | type    | description|
| ------------- |---------| :----------------------|
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

**Query params example:**

```json
{
  "query":{
    "userId":"5b0525134c0319001573485e",
    "userIds":["5afd6d369a88ff00190baf79", "5afd6d369a88ff22190baf79"]
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query":{"userId":"5b0525134c0319001573485e"}}' https://api.workonflow.com/333ccc134c0319001573485e/contact/get
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
