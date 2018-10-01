# Contact requests

### contact/create

**Метод для создания контактов**

```js
  https://botapi.workonflow.com/{teamid}/contact/create/{body}
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| :---------------------- |----:|
| basicData     | object        | Takes an object with the name of the contact | yes
| customFields  | array         | Field for adding channels to the contact, содержит в себе объекты содержащие не типичную информацию о пользователе |

|customFields|| |
|-----|----|-----|
| label         | string        | name of custom field   |
| value         | string        | value of custom field  |
| type          | string        | type of custom field   |
| id            | string        | uniq id for custom field |

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
  curl -H "Content-Type: application/json" -X POST -d '{ "basicData": {"name": "Alex", "email": "email@email.com"}, "customFields": [{"id": "B1R5NTS3z", "label": "Company", "value": "", "type": "company"}, {"id": "B1l094TB2M", "label": "Work phone", "value": "", "type": "phone"}, {"id": "rkbA9VTH3M", "label": "Work e-mail", "value": "", "type": "email"}] }' https://botapi.workonflow.com/333ccc134c0319001573485e/contact/create
```

**Response:**

```js
  { code: 200, message: "OK", data: { contactId: '1491eh1029318du1dqw9' } }
```
---

## contact/local

**Метод для получения "языка" пользователя**

```js
  https://botapi.workonflow.com/{teamid}/contact/local/{body}
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------:| ----:|
| userId     | string        | id of user | yes |

**Body message example:**
```json
{
  "userId":"5b0525134c0319001573485e"
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "userId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/contact/create
```

**Response:**

```js
  { code: 200, message: "OK", data: { userId: "5b0525134c0319001573485e", local: "us" } }
```
---
## contact/get

**Метод для получения пользоватей**
```js
  https://botapi.workonflow.com/{teamid}/contact/read/{body}
```

**Parameters:**
> **Warning!** One of the fields (userId or userIds) required

| field         | type    | description|
| ------------- |---------| ----------------------:|
| userId        | string  | Contact or user ID     |
| userIds       | array   | Several contact or user IDs|
| billingType   | string  | type of users: users, contacts or bots |

**Body message example:**

```json
{
  "userId":"5b0525134c0319001573485e",
  "userIds":["5afd6d369a88ff00190baf79", "5afd6d369a88ff22190baf79"],
  "billingType": "users" // or "contacts", "bots"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "billingType" : "users" }' https://botapi.workonflow.com/333ccc134c0319001573485e/contact/read
```
**Response:**

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
