# Mail requests

## Метод для получения информации о существующих почтовых каналов
```https://botapi.workonflow.com/{teamid}/channel.mail/account.get```

### Параметры:
| name      |type            | description                       | required |
| ------------- |---------------| ----------------------|---:|
| id        | string        | индетификатор канала. Вернет запрашиваемый объект. | no |
| ids       | array         | Массив индетификаторов канала. Вернет массив запрашиваемых объектов. (optionally)  | no |
| email         | string        | Почтовый логин. Вернет объект, совпадающий с почтовым логином. | no |
| isPrivate         | bool        | Вернет массив объектов: все приватные (если указано true), или публичные (если указано false) почтовые каналы | no |

### Пример тела запроса:
```json
  {
    "email": "email@email.com"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "email":"email@email.com" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.mail/account.get```

### Ответ:
```json
 {
  "code": 200,
  "message": "OK",
  "data":
   [ { "_id": "5a0ac1e74673cb4d73e5bde3",
       "email": "email@email.com",
       "name": "My postman-channel",
       "private": false,
       "userId": "59e5fafd8bd74500195f7da0",
       "outgoing": true,
       "streamId": "59e9c89c2cc5b200164e8398",
       "server": "email.com",
       "teamId": "333ccc134c0319001573485e",
       "status": true,
       "error": false,
       "seenBy": [Array],
       "visibleInStreams": [Array],
       "outgoingStreams:" [Array],
       "isVisibleToAll": true }
   ]
  }
```

> ### Если сделать запрос с пустым объектом - вернется массив объектов не приватных почтовых каналов:

# Метод для получения информации о письмах
```https://botapi.workonflow.com/{teamid}/channel.mail/read```

### Параметры:
> **Внимание!** Один из параметров обязательно должен быть передан: id, ids, type

|  name          |    type  |  description  | required |
| ------------- |---------------| ----------------------:|----:|
| id        | string        | идентификатор письма. Вернет объект письма. | |
| ids       | array         | Массив индетификаторов писем. Вернет массив объектов писем | |
| type      | string        | В зависимости от типа (outgoing/incoming) вернет все исходящие или входящие письма| |

### Пример тела запроса:
```json
  {
    "id": "5b0525134c0319001573485e",
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "id":"5b0525134c0319121573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.mail/read```

### Ответ:
```json
  {
    code: 200,
    message: OK,
    data: [{
      accountId: "channel id",
      attachments: [],
      cc: null,
      conversationId: "conversation id",
      date: "create date", // example format Fri, 20 Apr 2018 11:53:18 +0300
      from: "ereskoe@list.ru",
      headers: "header",
      html: "html mail",
      inReplyTo: null,
      messageId: "message id in mail client format", // example <1524214398.529320890@f338.i.mail.ru>
      name: "contact name",
      receivedDate: "date response mail", // example format Fri, 20 Apr 2018 11:53:18 +0300
      references: null,
      streamId: "",
      subject: "subject title mail",
      teamId: "team id",
      text: "text mail",
      threadId: "thread id",
      to: "channel mail",
      type: "incoming",
      _id: "5b0525134c0319121573485e",
    }
   ]
  }
```

# Telephony

# Создание SIP-юзера
```https://botapi.workonflow.com/{teamid}/channel.telephony/create```

### Параметры:
|  name   |  type  | description | required |
| ------------- |---------------| ----------------------:|---:|
| username        | string        | имя юзера | yes |
| password          | string        | пароль юзера  | yes |
| domain          | string        | домен  | yes |
| contactId          | string        | идентификатор юзера  | yes |

### Пример тела запроса:
```json
  {
    "username": "John Wick",
    "password": "somePassForJohn",
    "domain": "john@pbx.com",
    "contactId":  "333ccc134c0319001543481e"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "username": "John Wick", "password": "somePassForJohn", "domain": "john@pbx.com", "contactId": "333ccc134c0319001543481e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/create```

### Ответ:
```json
  {
    "code": 201,
    "message": "Channel created",
    "data": { "id": "33s231134c0319001543481e" }
  }
```

# Метод для удаления SIP-юзера (находится в разработке)
```https://botapi.workonflow.com/{teamid}/channel.telephony/delete```

### Параметры:
|  name   |  type  |   description  | required |
| ------------- |---------------| ----------------------:|---:|
| sipId        | string        | SIP ID | yes|

### Пример тела запроса:
```json
  {
    "sipId":  "333cbv134c0319001543481e"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "sipId": "333cbv134c0319001543481e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/delete```

### Ответ:
```json
  {
    code: 200,
    message: OK
  }
```


# Метод для получения SIP-юзера
```https://botapi.workonflow.com/{teamid}/channel.telephony/get```

### Параметры:
|  name       |  type  | description   | required |
| ------------- |---------------| ----------------------:|---:|
| username        | string        | имя юзера |
| sipId          | string        | идентификатор SIP-аккаунта  |
| contactId          | string        | идентификатор юзера  |

### Пример тела запроса:
```json
  {
    "sipId": "58"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "sipId": "58" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/get```

### Ответ:
```json
{
  "code": 200,
  "message": "OK",
  "data":
   [ {
     "id": 58,
     "username": "5a2668c0906f27001ce5ae54",
       "domain": "develop.workonflow.com",
       "email_address": "",
       "rpid": null,
       "teamId": "59e5f928ef5fcf001cfd5cef",
       "constactId": null,
       "contactId": "5a2668c0906f27001ce5ae54",
       "alias": "",
       "enable": null,
       "product": "workonflow"
     }
   ]
}
```

> ### Если сделать запрос с пустым объектом - вернется массив объектов SIP-аккаунтов:

# Метод для обновления SIP-юзера
```https://botapi.workonflow.com/{teamid}/channel.telephony/update```

### Параметры:
|  name      |  type  | description   | required |
| ------------- |---------------| ----------------------:|-----:|
| username        | string        | имя юзера | yes |
| password          | string        | пароль юзера  | yes |
| domain          | string        | домен  | yes|
| contactId          | string        | идентификатор юзера  | yes |
| sipId               | string      | идентификатор SIP-аккаунта | yes |

### Пример тела запроса:
```json
  {
    "username": "John Wick",
    "password": "somePassForJohn",
    "domain": "john@pbx.com",
    "contactId": "333ccc134c0319001543481e",
    "sipId": "111"
  }
```
### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "username": "John Wick", "password": "somePassForJohn", "domain": "john@pbx.com", "contactId": "333ccc134c0319001543481e", "sipId": "111" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/update```

### Ответ:
```json
  {
    code: 200,
    message: OK
  }
```
