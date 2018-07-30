# Stream requests

## stream/create

**Метод для создания потока.**
```js
  api.workonflow.com/{teamid}/stream/create/{query}
```

**Parameters:**
| field         | type    | description|
| ------------- |---------| :----------------------|
| name          | string  | new name for stream   |
| isEmpty       | boolean | по умолчанию поток создаётся с 3мя статусами, если указать данный параметр будет создан пустой поток  |

**Query params example:**

```json
{
  "query":{
    "name": "New stream",
    "isEmpty": "true"
  }
}
```
**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "name":"New stream" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream/create
```

**Response example:**
```js
 { code: 200, message: 'OK', data: { streamId: '5b0525134c0319001573485e' } }
```
----------------------------------------------------------------------------------------------------

## stream/delete
```js
  api.workonflow.com/{teamid}/stream/delete/{query}
```

**Parameters:**

| field         | type          | description         |
| ------------- |---------------| :------------------ |
| streamId      | string        | uniq id of stream   |

**Query params example:**

```json
{
  "query": {
    "streamId": "5b0525134c0319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream/delete
```

**Response example:**
```js
 { code: 200, message: 'OK' }
```
----------------------------------------------------------------------------------------------------

## stream/read

**Метод для получения потоков**

```js
  api.workonflow.com/{teamid}/stream/read/{query}
```

**Parameters:**

| field         | type            | description                        |
| ------------- |---------------  | :----------------------            |
| streamId      | string          | uniq id of stream (optionally)     |
| streamIds     | array of string | array uniq ids of stream  (optionally)|
| name          | string          | name of stream                     |
| roles         | array of string | список участников потока           |
| statuses      | array of string | список статусов потока             |
| settings      | array of object | список настроек потока содержит в себе настройки виджетов и оповещений, которые будут отображатся на панели задачи|
| widgets       | object          | объект состояния виджетов, каждый виджет содержит в себе тип и его активность |
| DataTime      | object          | при включении виджета отображает дедлайн или период времени для выполнения задачи |
| Priority      | object          | при включении отображает виджет важность задачи |
| Responsible   | object          | при включении отображает виджет ответственного за задачу |
| WorkflowStatus| object          | при включении отображает виджет статуса задачи |
| StreamSelect  | object          | при включении отображает виджет выбора потока бля задачи |
| Customers     | object          | при включении отображает виджет клиентов задачи |
| Points        | object          | при включении отображает виджет оценки задачи |
| notify        | object          | показывает состояния оповещения по изменениям в потоке |
| teamId        | string          | id of team |
| owner         | string          | id of user который создал поток |
| isPrivate     | boolean         | приватность стрима (при значении false поток будет доступен для всех участников team) |
| createdAt     | number          | дата создания стрима в формате timestamp (пример: 1516360789475) |
| updatedAt     | number          | дата последнего обновления в формате timestamp (пример: 1516360789475)|
| admins        | array of object | список администраторов потока |


**Query params example:**

```json
{
  "query":{
    "streamId": "5b0525134c0319001573485e",
    "streamIds": ["5b0525134c0319001573485e", "5b0525134c0319001573485e"]
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream/read
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
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
----------------------------------------------------------------------------------------------------


## stream.name/set

**Метод для того что-бы задать или изменить имя потока**

```js
  api.workonflow.com/{teamid}/stream.name/set/{query}
```

**Parameters:**

| field      | type      | description                        |
| ---------- |-----------| :-------------------|
| streamId   | string    | uniq id of stream   |
| name       | string    | new name for stream |

**Query params example:**
```json
{
  "query":{
    "streamId":"5b0525134c0319001573485e",
    "name":"For sales"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "name":"For sales" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.name/set
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
----------------------------------------------------------------------------------------------------

## stream.member/set.admin

**Метод для предоставления прав администратора участнику потока**
```js
  api.workonflow.com/{teamid}/stream.member/set.admin/{query}
```

**Parameters:**

| field      | type      | description         |
| ---------- |-----------| :-------------------|
| streamId   | string    | uniq id of stream   |
| userId     | string    | uniq id of user для предоставления прав |

**Query params example:**

```json
{
  "query":{
    "streamId": "5b0525134c0319001573485e",
    "userId": "5b0525134c0319001573426a"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.member/set.admin
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
----------------------------------------------------------------------------------------------------


## stream.member/revoke.admin

**Метод для изъятия прав администратора у участника потока**

```js
  api.workonflow.com/{teamid}/stream.member/revoke.admin/{query}
```

**Parameters:**

| field      | type      | description         |
| -----------|-----------| :----------------------|
| streamId   | string    | uniq id of stream |
| userId     | string    | uniq id of user для изъятия прав администратора |

**Query params example:**

```json
{
  "query":{
    "streamId":"5b0525134c0319001573485e",
    "userId":"5b1535134c0319001573485e"
  }
}
```
**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.member/revoke.admin
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
----------------------------------------------------------------------------------------------------

## stream.member/add

**Метод для добавления участника в поток**

```js
  api.workonflow.com/{teamid}/stream.member/add/{query}
```

**Parameters:**

| field      | type      | description                 |
| ---------- |-----------| :----------------------     |
| streamId   | string    | uniq id of stream           |
| userId     | string    | uniq id of user которого приглашают в поток  |

**Query params example:**

```json
{
  "query":{
    "streamId":"5b0525134c0319001573485e",
    "userId":"5b0635434c0319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.member/add
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
----------------------------------------------------------------------------------------------------

# Stream remove member
```js
  api.workonflow.com/{teamid}/stream.member/remove/{query}
```

**Parameters:**

| field     | type   | description                     |
| --------- |--------| :-------------------------------|
| streamId  | string | uniq id of stream               |
| userId    | string | uniq id of user, которого необходимо удалить из участников потока|

**Query params example:**

```json
{
  "query":{
    "streamI":"5b0525134c0319001573485e",
    "userId":"5b0534256c0319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "userId":"5b0525134c0319001573426a" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.member/remove
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
----------------------------------------------------------------------------------------------------


## stream.description/set

**Метод для добавления или изменения описания потока**

```js
  api.workonflow.com/{teamid}/stream.description/set/{query}
```

**Parameters:**

| field     | type          | description                     |
| --------- |---------------| :----------------------|
| streamId  | string        | uniq id of stream      |
| content   | string        | some text for description |

**Query params example:**

```json
{
  "query":{
    "streamId":"5b0525134c0319001573485e",
    "content":"new description for stream"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "content":"new description for stream" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.description/set
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
----------------------------------------------------------------------------------------------------


## stream.description/get

**Метод для добавления или изменения описания потока**

```js
  api.workonflow.com/{teamid}/stream.description/get/{query}
```

**Parameters:**

| field     | type          | description                     |
| --------- |---------------| :---------------------|
| streamId  | string        | uniq id of stream   |

**Query params example:**

```json
{
  "query":{
    "streamId":"5b0525134c0319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.description/get
```

**Response example:**
```js
  { code: 200, massage: 'OK', data:{ content: 'description stream' } }
```
----------------------------------------------------------------------------------------------------

## stream.status/create

**Метод для создания нового статуса в потоке**

```js
  api.workonflow.com/{teamid}/stream.status/create/{query}
```

**Parameters:**

| field     | type      | description           |
| --------- |-----------| :---------------------|
| name      | string    | new name for status   |
| streamId  | string    | uniq id of stream     |
| type      | string    | on of the types: Wait, In Progress, Done|
| color     | string    | Color of status in the format: #c0c0c0 |
| statusId  | string    | uniq id of new status in response |

**Query params example:**

```json
{
  "query":{
    "name": "End job",
    "streamId": "5b0525134c0319001573485e",
    "type": "Done",
    "color": "#c0c0c0"
  }
}
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "streamId":"5b0525134c0319001573485e", "name":"End job", "type":"Done", "color":"#c0c0c0" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.status/create
```

**Response example:**
```js
  { code: 200, message: 'OK', data: { statusId: '5b0525134c0319001573485e' } }
```
----------------------------------------------------------------------------------------------------

## stream.status/get

**Метод для получения статусов потока**

```js
  api.workonflow.com/{teamid}/stream.status/get/{query}
```

**Parameters:**

| field     | type     | description            |
| --------- |----------| :----------------------|
| streamId  | string   | uniq id of stream (optionally)|
| statusId  | string   | uniq id of status      |
| name      | string   | status name            |
| type      | string   | on of the types: Wait, In Progress, Done|
| color     | string   | Color of status in the format: #c0c0c0 |
| statusId  | string   | uniq id of new status in response |

**Query params example:**

```json
{
  "query":{
    "streamId":"5b0525134c0319001573485e",
    "statusId":"5b0525134c0319001573456s"
  }
}
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "statusId":"5b0525134c0319001573485e" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.status/get
```

**Response example:**
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
----------------------------------------------------------------------------------------------------

## stream.status/set.name

**Метод для добавления или изменения имени статуса потока**

```js
  api.workonflow.com/{teamid}/stream.status/set.name/{query}
```

**Query params example:**

| field     | type          | description            |
| --------- |---------------| :------------------ |
| statusId  | string        | uniq id of status   |
| name      | string        | new name for status |

**Query example:**

```json
{
  "query":{
    "statusId":"5b0525134c0319001573456s",
    "name": "Testing",
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "statusId":"5b0525134c0319001573485e", "name":"Testing" }}' https://api.workonflow.com/333ccc134c0319001573485e/stream.status/set.name
```

**Response example:**
```js
  { code: 200, message: 'OK' }
```
----------------------------------------------------------------------------------------------------


## stream.status/delete
**Метод для удаления статуса у потока**
```js
  api.workonflow.com/{teamid}/stream.status/delete/{query}
```

**Query params example:**

| field     | type    | description         |
| --------- |---------| :-------------------|
| streamId  | string  | uniq id of stream   |
| statusId  | string  | uniq id of status   |

**Query example:**
```json
{
  "query":{
    "streamId": "5b0526a34c0319001573456s",
    "statusId": "5b0525134c0319001573456s"
  }
}
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
---------------------------------------------------------------------------------------------

## stream.field/set

**Метод для включения/отключения вилжетов стрима**
```js
  api.workonflow.com/{teamid}/stream.field/set/{query}
```

**Query params example:**

| field     | type    | description         |
| --------- |---------| :-------------------|
| streamId  | string  | uniq id of stream   |
| budget    | boolean | on/off field (optionally) |
| deadline  | boolean | on/off field (optionally) |
| priority  | boolean | on/off field (optionally) |
| points    | boolean | on/off field (optionally) |
| timetoc   | boolean | on/off field (optionally) |

**Query example:**
```json
{
  "query":{
    "streamId":"5b0526a34c0319001573456s",
    "budget":"false",
    "deadline":"false",
    "priority":"true",
    "points":"false",
    "timetoc":"false"

  }
}
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
-----------------------------------------------------------------------------------

## stream.channels/use.default

**Метод для изменения канала в потоке**
```js
  api.workonflow.com/{teamId}/stream.channels/use.default/{query}
```

**Query params example:**

| field     | type    | description        |
| --------- |---------| :------------------|
| streamId  | string  | uniq id of stream  |
| channelId | string  | uniq id of channel |

**Query example:**
```json
{
  "query":{
    "streamId":"5b0526a34c0319001573456s",
    "channelId":"5b1635134c0319001573456s"
  }
}
```

**Response example:**
```js
  { code: 200, massage: 'OK' }
```
