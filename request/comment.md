# Comments requests

## Метод для получения колличества комментариев

```https://botapi.workonflow.com/{teamid}/comment/count```

### Параметры:
> **Внимание!** Один из параметров обязательно должен быть передан: threadId, threadIds, streamId

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | идентификатор треда        |
| threadIds     | array         | массив идентификаторов треда |
| streamId      | string        | идентификатор стрима        |

### Пример тела запроса:

```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/comment/count```

### Ответ:

```json
  { "code": 200, "message": "OK", "data": { "count": 1 } }
```

## Метод для создания комментариев
```https://botapi.workonflow.com/{teamid}/comment/create```

### Параметры:
> **Важно!** Должен быть только один параметр получателя: streamId, threadId или to

| field         | type     | description|
| ------------- |----------|----------------------|
| threadId      |string    | идентификатор треда. передаем, если комментарий необходимо создать в задаче |
| streamId      |string    | идентификатор стрима. передаем, если комментарий необходимо создать в потоке |
| to            |string    | идентификатор юзера. передаем, если комментарий необходимо отправить в личные сообщения |
| text          |string    | содержимое комментария |
| type          | STRING  | тип комментария: text, file, image |
| isPublic      | bool     |  при значении true - отправится письмо, если к стриму подключена почта |


### Пример тела запроса:
```json
{
  "to": "5971f31881d3f800149760b4",
  "text": "new comment",
}
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "to":"5971f31881d3f800149760b4", "text": "new comment" }' https://botapi.workonflow.com/333ccc134c0319001573485e/comment/create```

### Пример ответа:
```json
  {
    "code": 200,
    "message": "OK",
    "data": { "commentId": "5971f31881d3f800149760b4" } }
```

## Метод для получения комментариев
```https://botapi.workonflow.com/{teamid}/comment/read```

### Параметры:
| field         | type          | description|
| ------------- |---------------|:----------------------|
| threadId      | string        | идентификатор треда    |
| streamId      | string        | идентификатор стрима    |
| commentId     | string        | идентификатор комментария   |
| skip          | number        | кол-во комментариев которые необходимо пропустить |
| type          | string        | тип комментария |

### Пример тела запроса:
```json
{
  "streamId": "5afd74659a88ff00190baf81",
  "type": "file"
}
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "streamId":"5afd74659a88ff00190baf81" }' https://botapi.workonflow.com/333ccc134c0319001573485e/comment/read```

### Пример ответа:

```json
{
  "code": 200,
  "message": "OK",
  "data": [ {
    "type": "file",
    "createdAt": 1520926199680,
    "to": [],
    "from": "",
    "att": "",
    "commentId": "id comment",
    "channel": null,
    "threadId": "some thread id",
    "streamId": "5afd74659a88ff00190baf81",
  }, {
    "type": "file",
    "createdAt": 1520926199680,
    "to": [],
    "from": "",
    "att": "",
    "commentId": "id comment",
    "teamId": "some time id",
    "channel": null,
    "threadId": "some thread id",
    "streamId": "5afd74659a88ff00190baf81",
  }
  ]
}
```

> ### Если сделать запрос с пустым объектом - вернется массив объектов всех комментариев в тиме
