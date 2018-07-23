### Support GET and POST HTTP methods

# Метод для получения колличества комментариев
```p api.workonflow.com/{teamid}/comment/count/{query} ```

### Query:
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread   |
| threadIds     | array         | array ids of thread   |
| streamId      | string        | id of stream |

### Query example:
```js
  threadId: '5b0525134c0319001573485e',
  threadIds: ['5afd6d369a88ff00190baf79', '5afd6d369a88ff22190baf79', '5afd6d369a88ff00190bas12', ...],
  streamId: '5afd74659a88ff00190baf81'
```

### RESPONSES:
| code        | message | description           |
|:------------|:--------|:----------------------|
| 200         | OK      | return count of comment. Example: count:1   |


# Метод для создания комментариев
```api.workonflow.com/{teamid}/comment/create/{query}```

### Query:
| field         | type          | description|
| ------------- |---------------|:----------------------|
| threadId      | string        | id of thread          |
| streamId      | string        | id of stream          |
| to            | string        | id of user            |
| att           | string/array  | принимает текст либо массив типа: [{ type: 'text' data: { text: 'string' } }] (type - тип сообщения может быть text, file. data - объект с текстом либо id файла) |

### Query example:
```js
  threadId: '5b0525134c0319001573485e',
  streamId: '5afd74659a88ff00190baf81',
  to: '5971f31881d3f800149760b4',
  att: 'new comment',
  att: [{ type: 'text' data: { text: 'new comment in array' } }],
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return id of comment. Example: id: 'commentId'   |


# Метод для получения комментариев
```api.workonflow.com/{teamid}/comment/read/{query}```

| field         | type          | description|
| ------------- |---------------|:----------------------|
| threadId          | string        | id of thread   |
| streamId      |   string      | id of stream |
| commentId       | string       | id of comment   |
| skip          | number         | кол-во комментариев которые необходимо пропустить (optionally) |
| type          | string        | type of comment |

### Query example:
```js
  threadId: '5b0525134c0319001573485e',
  streamId: '5afd74659a88ff00190baf81',
  commentId: '5971f31881d3f800149760b4',
  skip: 100,
  type: 'file',
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return array of comments. Example see below   |

```js
  data: [ {
    type: 'type comment',
    createdAt: 1520926199680,
    updatedAt: 1520926199680,
    to: [],
    from: '',
    metadata: [],
    att: [],
    _id: 'id comment',
    teamId: 'some time id',
    channel: null,
    threadId: 'some thread id',
    streamId: 'some thread id',
  } ]
```