# Stream requests

## stream/create

**Метод для создания потока.**
```js
  https://botapi.workonflow.com/{teamid}/stream/create
```

**Parameters:**
| field         | type    | description| required |
| ------------- |---------| :----------------------|----:|
| name          | string  | new name for stream   | yes |
| isEmpty       | boolean | по умолчанию поток создаётся с 3мя статусами, если указать данный параметр будет создан пустой поток  |

**Body message example:**

```json
{
  "name": "New stream",
  "isEmpty": "true"
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "name":"New stream" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream/create
```

**Response:**
```js
 { code: 200, message: 'OK', data: { streamId: '5b0525134c0319001573485e' } }
```


## stream/delete
```js
  https://botapi.workonflow.com/{teamid}/stream/delete
```

**Parameters:**

| field         | type          | description         | required |
| ------------- |---------------| :------------------ |---: |
| streamId      | string        | uniq id of stream   | yes |

**Body message example:**

```json
{
  "streamId": "5b0525134c0319001573485e"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream/delete
```

**Response:**
```js
 { code: 200, message: 'OK' }
```


## stream/read

**Метод для получения потоков**

```js
  https://botapi.workonflow.com/{teamid}/stream/read
```

**Parameters:**
> **Warning!** One of the fields (streamId or streamIds) required

| field         | type            | description                        |
| ------------- |---------------  | :----------------------            |
| streamId      | string          | uniq id of stream (optionally)     |
| streamIds     | array of string | array uniq ids of stream  (optionally)|


**Body message example:**

```json
{
  "streamId": "5b0525134c0319001573485e",
  // or
  "streamIds": ["5b0525134c0319001573485e", "5b0525134c0319001573485e"]
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId" : "5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream/read
```

**Response:**

```js
{
  code: 200,
  message: 'OK',
  data: [ {
    streamId: '5b0525134c0319001573485e',
    name: 'stream name',
    roles: ['5b0525134c0319001573485e', '5b0525134c0319001573485e'],
    statuses: ['5b0525134c0319001573485e', '5b0525134c0319001573485e'],
    settings: [{
      widgets: {
        DataTime: { on: true, options: 'deadline', type: 'DataTime' },
        Priority: { on: true, type: 'Priority' },
        Responsible: { on: true, type: 'Responsible' },
        WorkflowStatus: { on: true, type: 'WorkflowStatus' },
        StreamSelect: { on: true, type: 'StreamSelect' },
        Customers: { type: 'Customers', on: true },
        Points: { type: 'Points', on: true }
      },
      notify: {}
    }],
    teamId: '5b0525134c0319001573485e',
    owner: '5b0525134c0319001573485e',
    isPrivate: true,
    createdAt: 1516360789475,
    updatedAt: 1516360789475,
    admins: ['5b0525134c0319001573485e', '5b0525134c0319001573485e']
  } ]
}
```



## stream.name/set

**Метод для того что-бы задать или изменить имя потока**

```js
  https://botapi.workonflow.com/{teamid}/stream.name/set
```

**Parameters:**

| field      | type      | description         | required |
| ---------- |-----------| :-------------------|----:|
| streamId   | string    | uniq id of stream   | yes |
| name       | string    | new name for stream | yes |

**Body message example:**
```json
{
  "streamId":"5b0525134c0319001573485e",
  "name":"For sales"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "name":"For sales" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.name/set
```

**Response:**
```js
  { code: 200, message: 'OK' }
```


## stream.member/set.admin

**Метод для предоставления прав администратора участнику потока**
```js
  https://botapi.workonflow.com/{teamid}/stream.member/set.admin
```

**Parameters:**

| field      | type      | description         | required |
| ---------- |-----------| :-------------------|----: |
| streamId   | string    | uniq id of stream   | yes |
| userId     | string    | uniq id of user для предоставления прав | yes |

**Body message example:**

```json
{
  "streamId": "5b0525134c0319001573485e",
  "userId": "5b0525134c0319001573426a"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/set.admin
```

**Response:**
```js
  { code: 200, message: 'OK' }
```


## stream.member/revoke.admin

**Метод для изъятия прав администратора у участника потока**

```js
  https://botapi.workonflow.com/{teamid}/stream.member/revoke.admin
```

**Parameters:**

| field      | type      | description         | required |
| -----------|-----------| :----------------------|-----:|
| streamId   | string    | uniq id of stream | yes |
| userId     | string    | uniq id of user для изъятия прав администратора | yes |

**Body message example:**

```json
{
  "streamId":"5b0525134c0319001573485e",
  "userId":"5b1535134c0319001573485e"
}
```
**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/revoke.admin
```

**Response:**
```js
  { code: 200, message: 'OK' }
```
----------------------------------------------------------------------------------------------------

## stream.member/add

**Метод для добавления участника в поток**

```js
  https://botapi.workonflow.com/{teamid}/stream.member/add
```

**Parameters:**

| field      | type      | description                 | required |
| ---------- |-----------| :----------------------     |---:|
| streamId   | string    | uniq id of stream           | yes |
| userId     | string    | uniq id of user которого приглашают в поток  | yes |

**Body message example:**

```json
{
  "streamId":"5b0525134c0319001573485e",
  "userId":"5b0635434c0319001573485e"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/add
```

**Response:**
```js
  { code: 200, message: 'OK' }
```


# Stream remove member
```js
  https://botapi.workonflow.com/{teamid}/stream.member/remove
```

**Parameters:**

| field     | type   | description                     | required |
| --------- |--------| :-------------------------------|----:|
| streamId  | string | uniq id of stream               | yes |
| userId    | string | uniq id of user, которого необходимо удалить из участников потока| yes |

**Body message example:**

```json
{
  "streamId":"5b0525134c0319001573485e",
  "userId":"5b0534256c0319001573485e"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.member/remove
```

**Response:**
```js
  { code: 200, message: 'OK' }
```

## stream.description/set

**Метод для добавления или изменения описания потока**

```js
  https://botapi.workonflow.com/{teamid}/stream.description/set
```

**Parameters:**

| field     | type          | description             | required |
| --------- |---------------| :----------------------|-------:|
| streamId  | string        | uniq id of stream      | yes |
| content   | string        | some text for description |

**Body message example:**

```json
{
  "streamId":"5b0525134c0319001573485e",
  "content":"new description for stream"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "content":"new description for stream" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.description/set
```

**Response:**
```js
  { code: 200, message: 'OK' }
```


## stream.description/get

**Метод для добавления или изменения описания потока**

```js
  https://botapi.workonflow.com/{teamid}/stream.description/get
```

**Parameters:**

| field     | type          | description            | required |
| --------- |---------------| :---------------------|-----:|
| streamId  | string        | uniq id of stream   | yes |

**Body message example:**

```json
  {
    "streamId":"5b0525134c0319001573485e"
  }
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.description/get
```

**Response:**
```js
  {
    code: 200,
    message: 'OK',
    data: {
      content: "{"type":"doc","content":[{"type":"paragraph","content":[{"type":"text","text":"Some description of stream"}]}]}"
      createdAt: 1525346261387
      editing: null
      format: "prosemirror"
      teamId: "5aeaefd59a88ff00190baccb"
      updatedAt: 1538385417996
      _id: "5b0525134c0319001573485e"
    }
  }
```


## stream.status/create

**Метод для создания нового статуса в потоке**

```js
  https://botapi.workonflow.com/{teamid}/stream.status/create
```

**Parameters:**

| field     | type      | description           | required |
| --------- |-----------| :---------------------|-----:|
| name      | string    | new name for status   | yes |
| streamId  | string    | uniq id of stream     | yes |
| type      | string    | on of the types: Wait, In Progress, Done| yes |
| color     | string    | Color of status in the format: #c0c0c0 |

**Body message example:**

```json
{
  "name": "End job",
  "streamId": "5b0525134c0319001573485e",
  "type": "Done",
  "color": "#c0c0c0"
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0525134c0319001573485e", "name":"End job", "type":"Done", "color":"#c0c0c0" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/create
```

**Response:**
```js
  { code: 200, message: 'OK', data: { statusId: '5b0525134c0319001533485e' } }
```
----------------------------------------------------------------------------------------------------

## stream.status/read

**Метод для получения статусов потока**

```js
  https://botapi.workonflow.com/{teamid}/stream.status/read
```

**Parameters:**
> **Warning!** One of the fields (streamId or statisId) required

| field     | type     | description            |
| --------- |----------| :----------------------|
| streamId  | string   | uniq id of stream (optionally)|
| statusId  | string   | uniq id of status      |

**Body message example:**

```json
{
  "streamId":"5b0525134c0319001573485e",
  // or
  "statusId":"5b0525134c0319001573456s"
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "statusId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/read
```

**Response:**
```js
  {
    code: 200,
    message: 'OK',
    data:[{
      color: "#c0c0c0",
      name: "End job",
      streamId: "5b0525134c0319001573485e",
      type: "Done",
      statusId: "5b0525134c0319001573485e"
    }]
  }
```

## stream.status/set.name

**Метод для добавления или изменения имени статуса потока**

```js
  https://botapi.workonflow.com/{teamid}/stream.status/set.name
```

**Parameters:**

| field     | type          | description            | required |
| --------- |---------------| :------------------ | ----:|
| statusId  | string        | uniq id of status   | yes |
| name      | string        | new name for status | yes |

**Body message example:**

```json
  {
    "statusId":"5b0525134c0319001573456s",
    "name": "Testing",
  }
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "statusId":"5b0525134c0319001573485e", "name":"Testing" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/set.name
```

**Response:**
```js
  { code: 200, message: 'OK' }
```

## stream.status/delete
**Метод для удаления статуса у потока**
```js
  https://botapi.workonflow.com/{teamid}/stream.status/delete
```

**Parameters:**

| field     | type    | description         | required |
| --------- |---------| :-------------------|----:|
| streamId  | string  | uniq id of stream   | yes |
| statusId  | string  | uniq id of status   | yes |

**Body message example:**
```json
  {
    "streamId": "5b0526a34c0319001573456s",
    "statusId": "5b0525134c0319001573456s"
  }
```
**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0526a34c0319001573456s", "statusId":"5b0525134c0319001573456s" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.status/delete
```

**Response:**
```js
  { code: 200, message: 'OK' }
```

## stream.field/set

**Метод для включения/отключения вилжетов стрима**
```js
  https://botapi.workonflow.com/{teamid}/stream.field/set
```

**Parameters:**

| field     | type    | description         | required |
| --------- |---------| :-------------------|----:|
| streamId  | string  | uniq id of stream   | yes |
| type      | string  | ones of types: Budget, DataTime, Priority, Points, TimeBudget, Responsible, WorkflowStatus, externalFollowers | yes |
| on        | bool    | on/off field        | yes |

**Body message example:**
```json
  {
    "streamId":"5b0526a34c0319001573456s",
    "type": "Budget",
    "on": true
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0526a34c0319001573456s", "type":"Budget", "on": true }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.field/set
```

**Response:**
```js
  { code: 200, message: 'OK' }
```


## stream.channels/use.default

**Метод для изменения канала в потоке**
```js
  https://botapi.workonflow.com/{teamId}/stream.channels/use.default
```

**Parameters:**

| field     | type    | description        | required |
| --------- |---------| :------------------|---:|
| streamId  | string  | uniq id of stream  | yes |
| channelId | string  | uniq id of channel | yes |

**Body message example:**
```json
{
  "streamId":"5b0526a34c0319001573456s",
  "channelId":"5b1635134c0319001573456s"
}
```
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5b0526a34c0319001573456s", "channelId":"5b1635134c0319001573456s" }' https://botapi.workonflow.com/333ccc134c0319001573485e/stream.channels/use.default
```

**Response:**
```js
  { code: 200, message: 'OK' }
```
