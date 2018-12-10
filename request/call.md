# Состояние: находится в разработке!

# Call requests

## Метод получения звонка
```https://botapi.workonflow.com/{teamid}/call/get```

### Параметры:
| field         | type          | description         | required |
| ------------- |---------------| -----------------   |----------|
| threadId      | string        | индетификатор треда        | yes      |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call/get```

### Пример ответа:
```json
{
  "code": 200,
  "message": "OK",
  "data":
  {
    "destinationId": "5bcda4d25ad71w0015771257",
    "streamId": "5bbc67c5522e2400149af76c",
    "originateUserId": "{"contactId":"5bcda4d2e74419001f6fe4b1","phone":"07112749","trunkId":"bambYXY3o"}",
    "typeDestination: "thread-incoming",
    "destinationContacts": "[{"contactId":"5b72aaab444507001c8be443","isMute":false,"isHold":false,"isMeInvite":false,"isExtension":false,"answered":false,"isBot":false,"hasOriginator":false},{"contactId":"2bcda4d2e74419001f6fe4f0","answered":true,"hasOriginator":true,"channelId":"558d25da-d6e4-11e8-bd3d-4799aea902e9","isMute":false,"createdAt":"1540203730669","isHold":false,"phone":"07112749","trunkId":"bambYVY3o","isMeInvite":false,"isExtension":false,"isBot":false}]"
  }
}
```

## Метод для приглашения пользователя(лей) в звонок
```https://botapi.workonflow.com/{teamid}/call.user/invite```

### Параметры:
> **Важно!** Обязательно передать в запросе: contactId или userIds

| field         | type          | description         | required |
| ------------- |---------------| -----------------   |----------|
| threadId      | string        | индетификатор треда        | yes      |
| contactId     | string     | индетификатор юзера             | yes       |
| phone         | string        | номер телефона          |
| userIds: ```[{ contactId, phone }]``` | array | массив объектов, состоящих из индетификатора юзера и телефона  | yes      |


### Пример тела запроса:
```json
  {
    "threadId": "5bcdb5535ad82d00157712c5",
    "contactId": "5b72aaab444507001b8sw553",
    "phone": "89999999999"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.user/invite```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для исключения пользовател(лей)/тредов и прочего
```https://botapi.workonflow.com/{teamid}/call/kick```

### Параметры:
| field         | type          | description         | required |
| ------------- |---------------| -----------------   |----|
| threadId      | string        | индетификатор треда        | yes |
| contactId        | string        | индетификатор юзера |
| phone       | string         | номер телефона  |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call/kick```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для постановки пользователя на паузу
```https://botapi.workonflow.com/{teamid}/call.user/hold```

### Параметры:
| field         | type          | description         | required |
| ------------- |---------------| -----------------   |---|
| threadId      | string        | индетификатор треда| yes |
| contactId        | string        | индетификатор юзера |
| phone       | number         | номер телефона  |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e",
    "contactId":"5b0525134c031900157348xd"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "contactId":"5b0525134c031900157348xd" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.user/hold```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для снятия пользователя с паузы
```https://botapi.workonflow.com/{teamid}/call/unpause```

### Параметры:
| field         | type          | description         | required |
| ------------- |---------------| -----------------   |---|
| threadId      | string        | индетификатор треда        | yes |
| contactId        | string        | индетификатор юзера          |
| phone       | number         | номер телефона  |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e",
    "contactId":"5b0525134c031900157348xd"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "contactId":"5b0525134c031900157348xd" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.user/unhold```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для загрузки и проигрывания аудиозаписи в звонке
```https://botapi.workonflow.com/{teamid}/call.audio/play```

### Параметры:
| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | индетификатор треда        |
| isLoop        | boolean       | должна (true) повторяться аудиозапись при звонке или нет (false) |
| url       | string        | адрес загруженного файла, для проигрывания |

> **Важно!** Аудиофайл должен иметь расширение mp3 или wav и не должен превышать размера в 10мб.

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e",
    "url": "https://url.to.your/audiofile.mp3",
    "isLoop": true
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "isLoop": true, "url": "https://url.to.your/audiofile.mp3"}' https://botapi.workonflow.com/333ccc134c0319001573485e/call.audio/play```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для остановки проигрывания аудиозаписи в звонке (для всех пользователей или для конкретных?)
```https://botapi.workonflow.com/{teamid}/call.audio/stop```

### Параметры:
| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | индетификатор треда        |
| url       | string        | адрес файла |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e",
    "url": "https://url.to.your/audiofile.mp3"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "url": "https://url.to.your/audiofile.mp3"}' https://botapi.workonflow.com/333ccc134c0319001573485e/call.audio/stop```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для начала записи разговора в звонке
```https://botapi.workonflow.com/{teamid}/call.recording/start```

### Параметры:
| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | индетификатор треда |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e",
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.recording/start```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

##Метод для остановки записи разговора в звонке
```https://botapi.workonflow.com/{teamid}/call.recording/stop```

### Параметры:
| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | индетификатор треда |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e",
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.recording/stop```

### Пример ответа:
```json
  { "code": 200, "message": "OK", "data": { "fileUrl": "https://url.to.your.recorded.dialog/audiofile.mp3" } }
```