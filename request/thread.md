# Thread requests

## thread/read

**Метод для получения информации по задаче**

```js
  api.workonflow.com/{teamid}/thread/read/{query}
```

**Parameters:**
| field      | type   | description|
| -----------|--------| :---------------------|
| threadId   | string | uniq id of thread      |
| statusId   | string | Status ID (returns all threads with the indicated status) (optionally)  |
| statusIds  | array  | array uniq ids of status (optionally) |
| streamId   | string |Stream ID (returns all threads in a stream) (optionally)    |
| ltUpdatedAt| number |(Less than) Time limit for creation > less than  (optionally)|
| gtUpdatedAt| number |(Greater than) Time limit for creation < greater than (optionally) |
| deadline   | array  | deadline of thread  |
|responsibleUserId|string|id of user ответственный за задачу |
| status     | string | id of status в котором находится задача |
| streamId   | string | id of stream в котором находится задача |
| teamId     | string | id of team    |
| customerId | string | id of customer, ксли он 1 |
| customerIds | array | список клиентов, если их несколько
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| roles      | array  | список участников задачи |
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |


**Query params example:**
```json
{
  "query":{
    "threadId":"5b0525134c0319001573485e",
    "statusId":"5b0321234c0319001573485e",
    "statusIds":["5afd6d369a88ff00190baf79", "5afd6d369a88ff22190baf79"],
    "streamId":"5afd74659a88ff00190baf81",
    "ltUpdatedAt":1256953732,
    "gtUpdatedAt":1256953732
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5afd6d369a88ff22190baf7x"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread/read
```

**Response example:**
```js
 {
   code: 200,
   message: 'OK',
   data: [{
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [],
    responsibleUserId: "",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
   }]
 }
```
-----------------------------------------------------------------------------

## thread/create

**Метод для создания задачи**

```js
  api.workonflow.com/{teamid}/thread/create/{query}
```

**Parameters:**
| field      | type   | description|
| ------------- |---------------| ----------------------:        |
| statusId      | string        | Status ID                      |
| streamId      | string        | Stream ID                      |
| title         | string        | name for thread                |
| deadline      | array         | deadline for task (optionally) |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |


**Query params example:**
```json
{
  "query":{
    "statusId": "5b0321234c0319001573485e",
    "streamId": "5afd74659a88ff00190baf81",
    "title": "New thread",
    "deadline": ["null", "1524902400000"],
    "responsibleUserId": "5afd74659a88ff0010988f81",
    "customerId": "5afd74659a88ff0010988f81",
    "roles": "5afd74659a88ff0010988f81"
  }
}
```


**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"title":"new thread", "streamId":"5afd74659a88ff00190baf81"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread/create
```

> Если не указывать statusId, задача будет создана в первый статус

**Response example:**

```js
  { code: 200, massage: 'OK', data: { threadId: '5afd74659a88ff0010900f81' } }
```
-----------------------------------------------------------------------------------

## thread.description/get

**Метод для получения описания задачи:**

```js
  api.workonflow.com/1/thread.description/get/{query}
```

**Parameters:**

| field      | type   | description|
| ---------- |--------| :---------------------- |
| threadId   | string | uniq id of thread      |
| content    | JSON   | JSON format example below in response |
| created    | number | дата создания в формате timestamp |
| teamId     | string | id of team   |
| descriptionId|string| id of description |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**

```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.desctiption/get
```

**Response example:**
```js
{
  code: 200,
  message: 'OK',
  data: [{
    content: "{}", // JSON format example below
    created: 1515487277798,
    teamId: "5b0321234c0319001573485f",
    descriptionId: "5b0321234c0319001573485x",
    threadId: "5b0321234c0319001573485e"
  }]

}
```

***example JSON description by content field:***

```
"{"type":"doc","content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"strike"}],"text":"text"}]},{"type":"paragraph"},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"underline"}],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"em"}],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"strong"}],"text":"text"}]},{"type":"ordered_check_list","content":[{"type":"check_list_item","attrs":{"isCheck":false},"content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]}]}]},{"type":"ordered_list","content":[{"type":"list_item","attrs":{"id":null},"content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]}]}]},{"type":"ordered_number_list","attrs":{"order":1},"content":[{"type":"list_item","attrs":{"id":null},"content":[{"type":"paragraph"},{"type":"horizontal_rule"},{"type":"paragraph"}]}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text text"}]}]}"
```
------------------------------------------------------------------------------------

## thread.descriprion/set

**Метод для добавления или ищменения описания задачи**
```js
  api.workonflow.com/1/thread.description/set/{query}
```

**Parameters:**
| field    | type   | description         |
| -------- |------- | :-------------------|
| threadId | string | id of thread        |
| content  | string | some text for description |
| descriptionId|string| id of description |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "content":"New description"
  }
}
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e", "content":"new description"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.desctiption/set
```

**Response example:**
```js
  { code: 200, message: 'OK', data: { descriptionId: '333ccc134c0319001573485x' } }
```
---------------------------------------------------------------------------------

## thread.fields.budget

**Метод для изменения бюджета задачи**

```js
  api.workonflow.com/{teamid}/thread.fields.budget/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| budget        | number        | Quantity of the thread’s budget |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "budget":100
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e", "budget":100}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.fields.budget
```

**Response example:**
```js
{
  code: 200,
  massage: 'OK',
  data: {
    budget: 100,
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [],
    responsibleUserId: "",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------

## thread.fields.deadline

**Метод для изменения дедлайна задачи**
```js
  api.workonflow.com/{teamid}/thread.fields.deadline/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| :---------------------|
| threadId      | string        | id of thread         |
| deadline      | array        | An array of data in the format of a time stamp. The first element is the start of the thread and the second is its end (if the first element is given a value of null, the thread will only display a deadline). |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "deadline":[null, 1524902400000]
  }
}
```


**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e", "deadline":[null, 1524902400000]}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.fields.deadline
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------

## thread.fields.priority

**Метод для изменения приоритета задачи**

```js
  api.workonflow.com/{teamid}/thread.fields.priority/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| priority        | string        | Priority level (one of two options: ‘HIGH’ or ‘NORMAL.’ Must be in upper case letters.) |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "priority":"HIGH"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e", "priority":"HIGH"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.fields.priority
```
**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    priority: 'HIGH',
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------


## thread.responsible/set

**Метод для изменения приоритета задачи**


```js
  api.workonflow.com/{teamid}/thread.responsible/set/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "userId":"5b032123210319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e", "userId":"5b032123210319001573485e"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.responsible/set
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "5b032123210319001573485e",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------

## thread.status/update

**Метод для изменения статуса задачи**

```js
  api.workonflow.com/{teamid}/thread.status/update/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| statusId        | string        | id of status |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "statusId":"5b032123210319001573485f"
  }
}
```


**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","statusId":"5b032123210319001573485f"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.responsible/set
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "5b032123210319001573485e",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------

## thread.points

**Метод для изменения статуса задачи**

```js
  api.workonflow.com/{teamid}/thread.points/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| points        | number        | number of points |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "points":20
  }
}
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","points":20}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.points
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "5b032123210319001573485e",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------

## thread.timetoc

**Метод для изменения времени завершения задачи**

```js
  api.workonflow.com/{teamid}/thread.timetoc/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| timetocompletion        | number        | timestamp |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "timetocompletion": 1524057338518
  }
}
```


**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","timetocompletion":1524057338518}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.timetoc
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "5b032123210319001573485e",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
----------------------------------------------------------------------------------

## thread.stream

**Метод для переноса задачи в другой поток**

```js
  api.workonflow.com/{teamid}/thread.stream/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| streamId        | string        | id of stream |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "streamId":"5b0321324c0319001573485e"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","streamId":"5b0321324c0319001573485e"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.stream
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    threadId: "5b0525134c0319001573485e",
    createdAt: 1524055334667,
    deadline: [null, 1524902400000],
    responsibleUserId: "5b032123210319001573485e",
    status: "5b0525134c0319001573485f",
    streamId: "5b0525134c0319001573485s",
    teamId: "5b0525134c0319001573485c",
    title: "title name",
    customerId: "5b0525134c0319001573485a",
    customerIds: [],
    commentsFilter: {},
    type: "Wait",
    roles: ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    updatedAt: 1524056052883,
  }
}
```
------------------------------------------------------------------------------------

## thread.title.set

**Метод изменения названия задачи**

```js
  api.workonflow.com/{teamid}/thread.title.set/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| title         | string        | new title for thread |

**Query params example:**
```json
{
  "query":{
    "threadId":"5b0321234c0319001573485e",
    "title":"New title for thread"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","title":"New title for thread"}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.title.set
```

**Response example:**
```js
  {code: 200, message: 'OK'}
```
-----------------------------------------------------------------------------------

## thread.customer/add

**Метод для добавления клиентав задачу**
```js
  api.workonflow.com/{teamid}/thread.customer/add/{query}
```

**Parameters:**
| field         | type     | description|
| ------------- |----------| ----------------------:|
| threadId      | string   | id of thread         |
| customerId    | string   | id of external user |
| customerIds   | array    | array of ids external users |

**Query params example:**
```json
{
  "query":{
    "threadId": "5b0321234c0319001573485e",
    "customerId": "5b0321324c0319001573485e",
    "customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]
  }
}
```


**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.customer/add
```

**Response example:**
```js
  {code: 200, message: "OK"}
```
-----------------------------------------------------------------------------------


# Thread remove customers
```js
  api.workonflow.com/{teamid}/thread.customer/remove/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| customerId    | string        | id of external user |
| customerIds   | array         | array of ids external users |

**Query params example:**
```json
{
  "query":{
    "threadId": "5b0321234c0319001573485e",
    "customerId": "5b0321324c0319001573485e",
    "customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]
  }
}
```


**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"threadId":"5b0321234c0319001573485e","customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]}}' https://api.workonflow.com/333ccc134c0319001573485e/thread.customer/remove
```

**Response example:**
```js
  {code: 200, message: 'OK'}
```
-----------------------------------------------------------------------------------



# Thread set followers
```js
  api.workonflow.com/{teamid}/thread.followers/set/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |

**Query params example:**
```json
{
  "query":{

  }
}
  threadId: '5b0321234c0319001573485e',
  userId: '5b0321324c0319001573485e'
```


**Query example:**



**Response example:**
```js
  {code: 200, message: 'OK'}
```
-----------------------------------------------------------------------------------



# Thread remove followers
```js
  api.workonflow.com/{teamid}/thread.responsible/followers/{query}
```

**Parameters:**
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |

**Query params example:**
```json
{
  "query":{

  }
}
  threadId: '5b0321234c0319001573485e',
  userId: '5b0321324c0319001573485e'
```


**Query example:**



**Response example:**
```js
  {code: 200, message: 'OK'}
```
