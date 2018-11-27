# Thread requests

## thread/read

**Метод для получения информации по задаче**

```js
  https://botapi.workonflow.com/{teamid}/thread/read
```

**Parameters:**

| field      | type   | description|
| -----------|--------| :---------------------|
| threadId   | string | uniq id of thread      |
| statusId   | string | Status ID (returns all threads with the indicated status)  |
| statusIds  | array  | array uniq ids of status |
| streamId   | string |Stream ID (returns all threads in a stream)    |
| ltUpdatedAt| number |(Less than) Time limit for creation > less than |
| gtUpdatedAt| number |(Greater than) Time limit for creation < greater than |
| deadline   | array  | deadline of thread  |
|responsibleUserId|string|id of user ответственный за задачу |
| status     | string | id of status в котором находится задача |
| streamId   | string | id of stream в котором находится задача |
| customerId | string | id of customer, eсли он 1 |
| customerIds | array | список клиентов, если их несколько
| title      | string | название задачи |
| type       | string | глобальный тип задачи Wait, inProgress, Done|
| roles      | array  | список участников задачи |
| createdAt  | number | дата создания в формате timestamp |
| updatedAt  | number | дата последнего обновления в формате timestamp |


**Body message example:**
```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5afd6d369a88ff22190baf7x" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/read
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

## thread/create

**Метод для создания задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread/create
```

**Parameters:**
| field      | type   | description| required |
| ------------- |---------------| ----------------------         |:----|
| statusId      | string        | Status ID                      | yes |
| streamId      | string        | Stream ID                      | yes |
| title         | string        | name for thread                ||
| deadline      | array         | deadline for task              ||
| responsibleUserId | string    | id of user responsible         ||
| customerId    | string        | id of external user            ||
| roles         | string        | id followers of the thread     ||
| description   | array         | принимает два вида объектов: { type: 'hashtag', name: '#имяхештега' }, { type: 'file', filename: 'имяФайла.txt', fileId: 'айди файла загруженного на амазон' }

**Body message example:**
```json
{
  "statusId": "5b0321234c0319001573485e",
  "streamId": "5afd74659a88ff00190baf81",
  "title": "New thread"
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "title":"New thread", "statusId": "5b0321234c0319001573485e","streamId":"5afd74659a88ff00190baf81" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/create
```

**Response example:**

```js
  { code: 200, massage: 'OK', data: { threadId: '5afd74659a88ff0010900f81' } }
```

## thread.description/read

**Метод для получения описания задачи:**

```js
  https://botapi.workonflow.com/thread.description/read
```

**Parameters:**

| field      | type   | description | required |
| ---------- |--------| :---------------------- |---:|
| threadId   | string | uniq id of thread      | yes |

**Body message example:**

```json
  {
    "threadId":"5b0321234c0319001573485e"
  }
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.desctiption/read
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

**Метод для добавления или изменения описания задачи**
```js
  https://botapi.workonflow.com/thread.description/set
```

**Parameters:**

| field    | type   | description         | required |
| -------- |------- | :-------------------|----:|
| threadId | string | id of thread        | yes |
| content  | string | some text for description | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "content":"New description"
  }
```

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "content":"new description" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.desctiption/set
```

**Response example:**
```js
  { code: 200, message: 'OK', data: { descriptionId: '333ccc134c0319001573485x' } }
```
---------------------------------------------------------------------------------

## thread.fields.budget

**Метод для изменения бюджета задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread.fields.budget
```

**Parameters:**

| field         | type          | description | required |
| ------------- |---------------| ----------------------:|----:|
| threadId      | string        | id of thread         | yes |
| budget        | number        | Quantity of the thread’s budget | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "budget":100
  }
```


```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "budget":100 }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.budget
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


## thread.fields.deadline

**Метод для изменения дедлайна задачи**
```js
  https://botapi.workonflow.com/{teamid}/thread.fields.deadline
```

**Parameters:**

| field         | type          | description | required |
| ------------- |---------------| :---------------------|---:|
| threadId      | string        | id of thread         | yes |
| deadline      | array        | An array of data in the format of a time stamp. The first element is the start of the thread and the second is its end (if the first element is given a value of null, the thread will only display a deadline). | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "deadline":[null, 1524902400000]
  }
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "deadline":[null, 1524902400000] }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.deadline
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


## thread.fields.priority

**Метод для изменения приоритета задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread.fields.priority
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| priority        | string        | Priority level (one of two options: ‘HIGH’ or ‘NORMAL.’ Must be in upper case letters.) | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "priority":"HIGH"
  }
```


```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "priority":"HIGH" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.priority
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


## thread.responsible/set

**Метод для назначения ответственного за тред**


```js
  https://botapi.workonflow.com/{teamid}/thread.responsible/set
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|----:|
| threadId      | string        | id of thread         | yes |
| userId        | string        | id of user | yes |

**Body message example:**
```json
{
  "threadId":"5b0321234c0319001573485e",
  "userId":"5b032123210319001573485e"
}
```


```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "userId":"5b032123210319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.responsible/set
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

## thread.responsible/remove

**Метод для назначения ответственного за тред**


```js
  https://botapi.workonflow.com/{teamid}/thread.responsible/remove
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|----:|
| threadId      | string        | id of thread         | yes |
| userId        | string        | id of user | yes |

**Body message example:**
```json
{
  "threadId":"5b0321234c0319001573485e",
  "userId":"5b032123210319001573485e"
}
```


```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "userId":"5b032123210319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.responsible/remove
```

**Response example:**

```js
{
  code: 200,
  massage: 'OK'
}
```

## thread.status

**Метод для изменения статуса задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread.status
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| statusId        | string        | id of status | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "statusId":"5b032123210319001573485f"
  }
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","statusId":"5b032123210319001573485f" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.status
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

## thread.fields.points

**Метод для изменения ранга задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread.fields.points
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| points        | number        | number of points | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "points":20
  }
```

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","points":20 }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.points
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

## thread.fields.timetoc

**Метод для изменения времени завершения задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread.fields.timetoc
```

**Parameters:**

| field         | type          | description|required|
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| timetocompletion        | number        | timestamp | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "timetocompletion": 1524057338518
  }
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","timetocompletion":1524057338518 }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.timetoc
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


## thread.stream

**Метод для переноса задачи в другой поток**

```js
  https://botapi.workonflow.com/{teamid}/thread.stream
```

**Parameters:**

| field         | type          | description|required|
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| streamId        | string        | id of stream | yes |

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "streamId":"5b0321324c0319001573485e"
  }
```


```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","streamId":"5b0321324c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.stream
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

## thread.title

**Метод изменения названия задачи**

```js
  https://botapi.workonflow.com/{teamid}/thread.title
```

**Parameters:**

| field         | type          | description| required|
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         |yes|
| title         | string        | new title for thread |yes|

**Body message example:**
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "title":"New title for thread"
  }
```


```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","title":"New title for thread" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.title
```

**Response example:**
```js
  {code: 200, message: 'OK'}
```
-----------------------------------------------------------------------------------

## thread.customer/add

**Метод для добавления клиентав задачу**
```js
  https://botapi.workonflow.com/{teamid}/thread.customer/add
```

**Parameters:**
> **Warning!** One of the fields (customerId or customerIds) required

| field         | type     | description| required |
| ------------- |----------| ----------------------|---:|
| threadId      | string   | id of thread         | yes |
| customerId    | string   | id of external user |
| customerIds   | array    | array of ids external users |

**Body message example:**
```json
  {
    "threadId": "5b0321234c0319001573485e",
    "customerId": "5b0321324c0319001573485e",
    // or
    "customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]
  }
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"] }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.customer/add
```

**Response example:**
```js
  {code: 200, message: "OK"}
```
-----------------------------------------------------------------------------------


# Thread remove customers
```js
  https://botapi.workonflow.com/{teamid}/thread.customer/remove
```

**Parameters:**
> **Warning!** One of the fields (customerId or customerIds) required

| field         | type          | description| required |
| ------------- |---------------| ----------------------|--:|
| threadId      | string        | id of thread         | yes |
| customerId    | string        | id of external user |
| customerIds   | array         | array of ids external users |

**Body message example:**
```json
  {
    "threadId": "5b0321234c0319001573485e",
    "customerId": "5b0321324c0319001573485e",
    "customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]
  }
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"] }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.customer/remove
```

**Response example:**
```js
  {code: 200, message: 'OK'}
```
-----------------------------------------------------------------------------------

# Thread set followers
```js
  https://botapi.workonflow.com/{teamid}/thread.followers/set
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| userId        | string        | id of user | yes |

**Body message example:**
```json
  {
    threadId: '5b0321234c0319001573485e',
    userId: '5b0321324c0319001573485e'
  }
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","userId": "5e1451234c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.followers/set
```

**Response example:**
```js
  {code: 200, message: 'OK'}
```
-----------------------------------------------------------------------------------

# Thread remove followers
```js
  https://botapi.workonflow.com/{teamid}/thread.followers/remove
```

**Parameters:**

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| userId        | string        | id of user | yes |

**Body message example:**
```json
{
  threadId: '5b0321234c0319001573485e',
  userId: '5b0321324c0319001573485e'
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","userId": "5b0321324c0319001573484q" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.followers/remove
```


**Response example:**
```js
  {code: 200, message: 'OK'}
```

# Add tag(s) to thread
```js
  https://botapi.workonflow.com/{teamid}/thread/pushtag
```

**Parameters:**
> **Warning!** One of the fields (tagId or tagIds) required

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| tagId        | string        | id of tag |  |
| tagIds        | array         | ids of tag  | |

**Body message example:**
```json
{
  "threadId": '5b0321234c0319001573485e',
  "tagId": '5b0321324c0319001573485e'
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","tagId": "5b0321324c0319001573484q" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/pushtag
```


**Response example:**
```js
  {code: 200, message: 'OK'}
```

# Remove tag(s) at thread
```js
  https://botapi.workonflow.com/{teamid}/thread/pulltag
```

**Parameters:**
> **Warning!** One of the fields (tagId or tagIds) required

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | id of thread         | yes |
| tagId        | string        | id of tag |  |
| tagIds        | array         | ids of tag  | |

**Body message example:**
```json
{
  "threadId": '5b0321234c0319001573485e',
  "tagId": '5b0321324c0319001573485e'
}
```

**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","tagId": "5b0321324c0319001573484q" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/pulltag
```


**Response example:**
```js
  {code: 200, message: 'OK'}
```
