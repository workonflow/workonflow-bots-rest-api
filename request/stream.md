# Stream requests

### Метод для создания потока.

```https://botapi.workonflow.com/{teamid}/stream/create```

### Параметры:
| field         | type    | description| required |
| ------------- |---------| :----------------------|----:|
| name          | string  | имя стрима   | yes |
| isEmpty       | boolean | по умолчанию поток создаётся с 3мя статусами, если указать данный параметр будет создан пустой поток, т.е. без статусов  |

### Пример тела запроса:
```json
{
  "name": "New stream",
  "isEmpty": "true"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "name":"New stream" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream/create```

### Пример ответа:
```json
 {
   "code": 200,
   "message": 'OK',
   "data": { "streamId": "5b0525134c0319001573485e" }
 }
```

### Метод для удаления потока

```https://botapi.workonflow.com/{teamid}/stream/delete```

### Параметры:
| field         | type          | description         | required |
| ------------- |---------------| :------------------ |---: |
| streamId      | string        | идентификатор стрима   | yes |

### Пример тела запроса:
```json
{
  "streamId": "5b0525134c0319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream/delete```

### Пример ответа:
```json
 { "code": 200, "message": "OK" }
```

## Метод для получения потоков

```https://botapi.workonflow.com/{teamid}/stream/read```

### Параметры:
> **Внимание!** Одно из полей обязательно должно быть передано в запросе: streamId или streamIds

| field         | type            | description                        |
| ------------- |---------------  | :----------------------            |
| streamId      | string          | индетификатор стрима     |
| streamIds     | array of string | массив индетификаторов стримов |

### Пример тела запроса:
```json
{
  "streamId": "5b0525134c0319001573485e",
}
```

### Пример запроса с помощью curl:

```curl -H "Content-Type: application/json" -X POST -d '{ "streamId" : "5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream/read```

### Пример ответа:

```json
{
  "code": 200,
  "message": "OK",
  "data": [ {
    "streamId": "5b0525134c0319001573485e",
    "name": "stream name",
    "roles": ["5b0525134c0319001573485e", "5b0525134c0319001573485e"],
    "statuses": ["5b0525134c0319001573485e", "5b0525134c0319001573485e"],
    "settings": [{
      "widgets": {
        "DataTime": { "on": true, "options": "deadline", "type": "DataTime" },
        "Priority": { "on": true, "type": "Priority" },
        "Responsible": { "on": true, "type": "Responsible" },
        "WorkflowStatus": { "on": true, "type": "WorkflowStatus" },
        "StreamSelect": { "on": true, "type": "StreamSelect" },
        "Customers": { "type": "Customers", "on": true },
        "Points": { "type": "Points", "on": true }
      },
      "notify": {}
    }],
    "teamId": "5b0525134c0319001573485e",
    "owner": "5b0525134c0319001573485e",
    "isPrivate": true,
    "createdAt": 1516360789475,
    "updatedAt": 1516360789475,
    "admins": ["5b0525134c0319001573485e", "5b0525134c0319001573485e"]
  } ]
}
```

## Метод изменения имени потока

```https://botapi.workonflow.com/{teamid}/stream.name/set```

### Параметры:
| field      | type      | description         | required |
| ---------- |-----------| :-------------------|----:|
| streamId   | string    | индетификатор стрима   | yes |
| name       | string    | новое имя стрима | yes |

### Пример тела запроса:
```json
{
  "streamId":"5b0525134c0319001573485e",
  "name":"For sales"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "name":"For sales" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.name/set```

### Пример ответа:
```json
  { "code": 200, "message": 'OK' }
```

## Метод для предоставления прав администратора участнику потока
```https://botapi.workonflow.com/{teamid}/stream.member/set.admin```

### Параметры:
| field      | type      | description         | required |
| ---------- |-----------| :-------------------|----: |
| streamId   | string    | индетификатор стрима   | yes |
| userId     | string    | индетификатор юзера для предоставления прав | yes |

### Пример тела запроса:
```json
{
  "streamId": "5b0525134c0319001573485e",
  "userId": "5b0525134c0319001573426a"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/set.admin```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для изъятия прав администратора у участника потока
```https://botapi.workonflow.com/{teamid}/stream.member/revoke.admin```

### Параметры:

| field      | type      | description         | required |
| -----------|-----------| :----------------------|-----:|
| streamId   | string    | индетификатор стрима | yes |
| userId     | string    | индетификатор юзера для лишения прав администратора | yes |

### Пример тела запроса:
```json
{
  "streamId":"5b0525134c0319001573485e",
  "userId":"5b1535134c0319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/revoke.admin```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для добавления участника в поток
```https://botapi.workonflow.com/{teamid}/stream.member/add```

### Параметры:
| field      | type      | description                 | required |
| ---------- |-----------| :----------------------     |---:|
| streamId   | string    | индетификатор стрима           | yes |
| userId     | string    | индетификатор юзера которого приглашают в поток  | yes |

### Пример тела запроса:
```json
{
  "streamId":"5b0525134c0319001573485e",
  "userId":"5b0635434c0319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/add```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для удаления участника стрима
```https://botapi.workonflow.com/{teamid}/stream.member/remove```

### Параметры:
| field     | type   | description                     | required |
| --------- |--------| :-------------------------------|----:|
| streamId  | string | индетификатор стрима               | yes |
| userId    | string | индетификатор юзера, которого необходимо удалить из участников потока| yes |

### Пример тела запроса:
```json
{
  "streamId":"5b0525134c0319001573485e",
  "userId":"5b0534256c0319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/remove```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для добавления или изменения описания потока
```https://botapi.workonflow.com/{teamid}/stream.description/set```

### Параметры:
| field     | type          | description             | required |
| --------- |---------------| :----------------------|-------:|
| streamId  | string        | индетификатор stream      | yes |
| content   | string        | some text for description | yes |

### Пример тела запроса:
```json
{
  "streamId":"5b0525134c0319001573485e",
  "content":"new description for stream"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "content":"new description for stream" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.description/set```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для добавления или изменения описания потока
```https://botapi.workonflow.com/{teamid}/stream.description/get```

### Параметры:
| field     | type          | description            | required |
| --------- |---------------| :---------------------|-----:|
| streamId  | string        | индетификатор стрима   | yes |

### Пример тела запроса:
```json
  {
    "streamId":"5b0525134c0319001573485e"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.description/get```

### Пример ответа:
```json
  {
    "code": 200,
    "message": "OK",
    "data": {
      "content": "{"type":"doc","content":[{"type":"paragraph","content":[{"type":"text","text":"Some description of stream"}]}]}",
      "createdAt": 1525346261387,
      "editing": null,
      "format": "prosemirror",
      "teamId": "5aeaefd59a88ff00190baccb",
      "updatedAt": 1538385417996,
      "_id": "5b0525134c0319001573485e"
    }
  }
```

## Метод для создания нового статуса в потоке
```https://botapi.workonflow.com/{teamid}/stream.status/create```

### Параметры:
| field     | type      | description           | required |
| --------- |-----------| :---------------------|-----:|
| name      | string    | имя статуса   | yes |
| streamId  | string    | индетификатор стрима     | yes |
| type      | string    | тип статуса: Wait, In Progress, Done| yes |
| color     | string    | цвет статуса в hex-формате: #c0c0c0 |

### Пример тела запроса:
```json
{
  "name": "End job",
  "streamId": "5b0525134c0319001573485e",
  "type": "Done",
  "color": "#c0c0c0"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "name":"End job", "type":"Done", "color":"#c0c0c0" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/create```

### Пример ответа:
```json
  { "code": 200, "message": "OK", "data": { "statusId": "5b0525134c0319001533485e" } }
```

## Метод для получения статусов потока
```https://botapi.workonflow.com/{teamid}/stream.status/read```

### Параметры:
> **Внимание!** Один из параметров обязательно должен быть передан в запросе: streamId или statisId

| field     | type     | description            |
| --------- |----------| :----------------------|
| streamId  | string   | индетификатор стриа|
| statusId  | string   | индетификатор статуса      |

### Пример тела запроса:
```json
{
  "streamId":"5b0525134c0319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "statusId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/read```

### Пример ответа:
```json
  {
    "code": 200,
    "message": "OK",
    "data":[{
      "color": "#c0c0c0",
      "name": "End job",
      "streamId": "5b0525134c0319001573485e",
      "type": "Done",
      "statusId": "5b0525134c0319001573485e"
    }]
  }
```

## Метод для добавления или изменения имени статуса потока
```https://botapi.workonflow.com/{teamid}/stream.status/set.name```

### Параметры:
| field     | type          | description            | required |
| --------- |---------------| :------------------ | ----:|
| statusId  | string        | индетификатор статуса   | yes |
| name      | string        | новое имя для статуса | yes |

### Пример тела запроса:
```json
  {
    "statusId":"5b0525134c0319001573456s",
    "name": "Testing",
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "statusId":"5b0525134c0319001573485e", "name":"Testing" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/set.name```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для удаления статуса у потока
```https://botapi.workonflow.com/{teamid}/stream.status/delete```

### Параметры:

| field     | type    | description         | required |
| --------- |---------| :-------------------|----:|
| streamId  | string  | индетификатор стрима   | yes |
| statusId  | string  | индетификатор статуса   | yes |

### Пример тела запроса:
```json
  {
    "streamId": "5b0526a34c0319001573456s",
    "statusId": "5b0525134c0319001573456s"
  }
```
### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0526a34c0319001573456s", "statusId":"5b0525134c0319001573456s" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/delete```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для включения/отключения вилжетов стрима
```https://botapi.workonflow.com/{teamid}/stream.field/set```

### Параметры:
| field     | type    | description         | required |
| --------- |---------| :-------------------|----:|
| streamId  | string  | индетификатор stream   | yes |
| type      | string  | ones of types: Budget, DataTime, Priority, Points, TimeBudget, Responsible, WorkflowStatus, externalFollowers | yes |
| on        | bool    | on/off field        | yes |

### Пример тела запроса:
```json
  {
    "streamId":"5b0526a34c0319001573456s",
    "type": "Budget",
    "on": true
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0526a34c0319001573456s", "type":"Budget", "on": true }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.field/set```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```

## Метод для изменения канала в потоке
```https://botapi.workonflow.com/{teamId}/stream.channels/use.default```

### Параметры:
| field     | type    | description        | required |
| --------- |---------| :------------------|---:|
| streamId  | string  | индетификатор stream  | yes |
| channelId | string  | индетификатор channel | yes |

### Пример тела запроса:
```json
{
  "streamId":"5b0526a34c0319001573456s",
  "channelId":"5b1635134c0319001573456s"
}
```
### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0526a34c0319001573456s", "channelId":"5b1635134c0319001573456s" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.channels/use.default```

### Пример ответа:
```json
  { "code": 200, "message": "OK" }
```
