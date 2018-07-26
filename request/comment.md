# Comments actions

### comment/count

**Метод для получения колличества комментариев**

```js
  api.workonflow.com/{teamid}/comment/count/{query}
```

**Parameters:**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| threadIds     | array         | array ids of thread |
| streamId      | string        | id of stream        |

**Query params example:**

```json
  {
    "query": {
      "threadId":"5b0525134c0319001573485e"
    }
  }
```

**Query example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "threadId":"5b0525134c0319001573485e" }}' https://api.workonflow.com/333ccc134c0319001573485e/comment/count
```

**Response example:**

```js
  { code: 200, message: "OK", data: { count: 1 } }
```

---

### comment/create

**Метод для создания комментариев**

```js
  api.workonflow.com/{teamid}/comment/create/{query}
```

**Parameters:**

| field         | type     | description|
| ------------- |----------|----------------------|
| threadId      |string    | id of thread указываем если комментарий необходимо создать в задаче |
| streamId      |string    | id of stream указываем если комнтарий необходимо создать в потоке |
| to            |string    | id of user указываем если комнтарий необходимо отправить в личные сообщения |
| att           |string/array| принимает текст либо массив типа: [{ type: 'text' data: { text: 'string' } }] (type - тип сообщения может быть text, file. data - объект с текстом либо id файла) |
| commentId     | string | идентификатор комментария, приходит в ответе на запрос |

> **Важно!** должен быть только один параметр получателя: streamId, threadId или to

**Query params example:**
```js
{
  to: '5971f31881d3f800149760b4',
  att: 'new comment'
}
```

**Query example:**
TODO

**Response example:**
```js
  { code: 200, massage: "OK", data: { commentId: '5971f31881d3f800149760b4' } }
```
---

### comment/read

**Метод для получения комментариев**

```js
  api.workonflow.com/{teamid}/comment/read/{query}
```

**Parameters:**

| field         | type          | description|
| ------------- |---------------|:----------------------|
| threadId      | string        | id of thread    |
| streamId      | string        | id of stream    |
| commentId     | string        | id of comment   |
| skip          | number        | кол-во комментариев которые необходимо пропустить (optionally) |
| type          | string        | type of comment |
| createdAt     | number        | время создания комментария в формате timestamp |
| to            | array         | id of user усли комментарий был отправлен в личные сообщения пользователю |
| from          | string        | id of user который создал комментарий |
| att           | string        | текст комментария |
| channel       | string/null   | id of channel, приходит в ответе если комментарий был создан с использованием внешнего канала |
**Query params example:**
```js
{
  threadId: '5b0525134c0319001573485e',
  streamId: '5afd74659a88ff00190baf81',
  commentId: '5971f31881d3f800149760b4',
  skip: 100,
  type: 'file',
}
```

**Query example:**
TODO

**Response example:**

```js
{
  code: 200,
  message: 'OK',
  data: [ {
    type: 'type comment',
    createdAt: 1520926199680,
    to: [],
    from: '',
    att: '',
    commentId: 'id comment',
    channel: null,
    threadId: 'some thread id',
    streamId: 'some thread id',
  }, {
    type: 'type comment',
    createdAt: 1520926199680,
    to: [],
    from: '',
    att: '',
    commentId: 'id comment',
    teamId: 'some time id',
    channel: null,
    threadId: 'some thread id',
    streamId: 'some thread id',
  }, ... ]
}
```



**Parameters:**
**Query params example:**
**Query example:**
**Response example:**
