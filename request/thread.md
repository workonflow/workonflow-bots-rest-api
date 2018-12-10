# Thread requests

## Метод для получения информации по задаче
```https://botapi.workonflow.com/{teamid}/thread/read```

### Параметры:
| field      | type   | description|
| -----------|--------| :---------------------|
| threadId   | string |  индетификатор треда      |
| statusId   | string | индетификатор статуса (возвращает все треды в указанном статусе)  |
| statusIds  | array  | массив индетификаторов статусов |
| streamId   | string | индетификатор стрима (возвращает все треды в указанном стриме)    |
| ltUpdatedAt| timestamp in seconds | возвращает все треды которые обновлялись раньше указанного времени |
| gtUpdatedAt| timestamp in seconds | возвращает все треды которые обновлялись позже указанного времени |
| deadline   | array  | возвращает треды с указанным дедлайном  |
|responsibleUserId|string| индетификатор ответственного за задачу |
| status     | string | индетификатор статуса в котором находится задача |
| streamId   | string | индетификатор стрима в котором находится задача |
| customerId | string | индетификатор клиента, eсли он один |
| customerIds | array | список клиентов, если их несколько
| title      | string | название задачи |
| type       | string | глобальный тип задачи: Wait, inProgress, Done|
| roles      | array  | список участников задачи |
| createdAt  | timestamp in seconds | дата создания в формате timestamp |
| updatedAt  | timestamp in seconds | дата последнего обновления в формате timestamp |

### Пример тела запроса:
```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5afd6d369a88ff22190baf7x" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/read```

### Пример ответа:
```json
  {
    "code": 200,
    "message": "OK",
    "data": [{
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [],
    "responsibleUserId": "",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
    }]
  }
```

## Метод для создания задачи
```https://botapi.workonflow.com/{teamid}/thread/create```

### Параметры:
| field      | type   | description| required |
| ------------- |---------------| ----------------------         |----:|
| statusId      | string        | индетификатор статуса                      | yes |
| streamId      | string        | индетификатор стрима                      | yes |
| title         | string        | имя задачи                | no|
| deadline      | array         | дедлайн задачи              |no|
| responsibleUserId | string    | индетификатор ответственного за задачу         |no|
| customerId    | string        | индетификатор внешнего кастомера            |no|
| roles         | string        | индетификатор(-ы) фолловеров задачи     |no|
| description   | array         | принимает два вида объектов: ```{ type: 'hashtag', name: '#имяхештега' }, { type: 'file', filename: 'имяФайла.txt', fileId: 'айди файла загруженного на амазон' }``` |no|

### Пример тела запроса:
```json
{
  "statusId": "5b0321234c0319001573485e",
  "streamId": "5afd74659a88ff00190baf81",
  "title": "New thread"
}
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "title":"New thread", "statusId": "5b0321234c0319001573485e","streamId":"5afd74659a88ff00190baf81" }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread/create
```

### Пример ответа:
```json
  { "code": 200, "message": "OK", "data": { "threadId": "5afd74659a88ff0010900f81" } }
```

## Метод для получения описания задачи:
```https://botapi.workonflow.com/thread.description/read```

### Параметры:

| field      | type   | description | required |
| ---------- |--------| ----------------------|---:|
| threadId   | string | индетификатор треда      | yes |

### Пример тела запроса:

```json
  {
    "threadId":"5b0321234c0319001573485e"
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/threaddesctiption/read```

### Пример ответа:
```json
{
  "code": 200,
  "message": "OK",
  "data": [{
    "content": "{}", // JSON format example. See below
    "created": 1515487277798,
    "teamId": "5b0321234c0319001573485f",
    "descriptionId": "5b0321234c0319001573485x",
    "threadId": "5b0321234c0319001573485e"
  }]
}
```

***example JSON description by content field:***
```json
"{"type":"doc","content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"strike"}],"text":"text"}]},{"type":"paragraph"},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"underline"}],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"em"}],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"strong"}],"text":"text"}]},{"type":"ordered_check_list","content":[{"type":"check_list_item","attrs":{"isCheck":false},"content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]}]}]},{"type":"ordered_list","content":[{"type":"list_item","attrs":{"id":null},"content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]}]}]},{"type":"ordered_number_list","attrs":{"order":1},"content":[{"type":"list_item","attrs":{"id":null},"content":[{"type":"paragraph"},{"type":"horizontal_rule"},{"type":"paragraph"}]}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text text"}]}]}"
```
------------------------------------------------------------------------------------

## Метод для добавления или изменения описания задачи
```https://botapi.workonflow.com/thread.description/set```

### Параметры:

| field    | type   | description         | required |
| -------- |------- | :-------------------|----:|
| threadId | string | индетификатор треда        | yes |
| content  | string | техт для описания задачи | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "content":"New description"
  }
```

```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "content":"new description" }' https://botapi.workonflow.com/333ccc134c0319001573485e/threaddesctiption/set```

### Пример ответа:
```json
  { "code": 200, "message": "OK", "data": { "descriptionId": "333ccc134c0319001573485x" } }
```

## Метод для изменения бюджета задачи**
```https://botapi.workonflow.com/{teamid}/thread.fields.budget```

### Параметры:
| field         | type          | description | required |
| ------------- |---------------| ----------------------:|----:|
| threadId      | string        | индетификатор треда         | yes |
| budget        | number        | бюджет задачи | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "budget":100
  }
```

### Пример запроса с помошью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "budget":100 }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.budget```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "budget": 100,
    "threadId": "5b0321234c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [],
    "responsibleUserId": "",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для изменения дедлайна задачи
```https://botapi.workonflow.com/{teamid}/thread.fields.deadline```

### Параметры:
| field         | type          | description | required |
| ------------- |---------------| :---------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| deadline      | array        | Массив состоит из двух элементов, в виде таймстампа в секундах. Первый элемент отвечает за старт задачи, второй элемент в массиве за дедлайн задачи (если первый элемент не указан, то просто отображается дедлайн, а не промежуток между датами). | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "deadline":[null, 1524902400000]
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "deadline":[null, 1524902400000] }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fieldsdeadline```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для изменения приоритета задачи
```https://botapi.workonflow.com/{teamid}/thread.fields.priority```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда | yes |
| priority        | string        | Приоритет задачи. Может быть либо ‘HIGH’,либо ‘NORMAL’. Обязательно передавать значение этого поля в верхнем регистре. | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "priority":"HIGH"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "priority":"HIGH" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fieldspriority```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "priority": 'HIGH',
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для назначения ответственного за тред
```https://botapi.workonflow.com/{teamid}/thread.responsible/set```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|----:|
| threadId      | string        | индетификатор треда | yes |
| userId        | string        | индетификатор  ответственного юзера | yes |

### Пример тела запроса:
```json
{
  "threadId":"5b0321234c0319001573485e",
  "userId":"5b032123210319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "userId":"5b032123210319001573485e" }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread.responsible/set
```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "5b032123210319001573485e",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для удаления ответственного за тред
```https://botapi.workonflow.com/{teamid}/thread.responsible/remove```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|----:|
| threadId      | string        | индетификатор треда         | yes |
| userId        | string        | индетификатор ответственного за тред | yes |

### Пример тела запроса:
```json
{
  "threadId":"5b0321234c0319001573485e",
  "userId":"5b032123210319001573485e"
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e", "userId":"5b032123210319001573485e" }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread.responsible/remove```

### Пример ответа:
```js
{
  "code": 200,
  "massage": "OK"
}
```

## Метод для изменения статуса задачи
```https://botapi.workonflow.com/{teamid}/thread.status```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| statusId        | string        | индетификатор статуса треда | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "statusId":"5b032123210319001573485f"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","statusId":"5b032123210319001573485f" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.status```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "5b032123210319001573485e",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для изменения ранга задачи
```https://botapi.workonflow.com/{teamid}/thread.fields.points```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда | yes |
| points        | number        | ранг задачи | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "points":20
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","points":20 }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.points```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "5b032123210319001573485e",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для изменения времени завершения задачи
```https://botapi.workonflow.com/{teamid}/thread.fields.timetoc```

### Параметры:
| field         | type          | description|required|
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| timetocompletion        | number        | таймстамп в секундах | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "timetocompletion": 1524057338518
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","timetocompletion":1524057338518 }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.fields.timetoc```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "5b032123210319001573485e",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод для переноса задачи в другой поток
```https://botapi.workonflow.com/{teamid}/thread.stream```

### Параметры:
| field         | type          | description|required|
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| streamId        | string        | индетификатор стрима | yes |

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "streamId":"5b0321324c0319001573485e"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","streamId":"5b0321324c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.stream```

### Пример ответа:
```json
{
  "code": 200,
  "massage": "OK",
  "data": {
    "threadId": "5b0525134c0319001573485e",
    "createdAt": 1524055334667,
    "deadline": [null, 1524902400000],
    "responsibleUserId": "5b032123210319001573485e",
    "status": "5b0525134c0319001573485f",
    "streamId": "5b0525134c0319001573485s",
    "teamId": "5b0525134c0319001573485c",
    "title": "title name",
    "customerId": "5b0525134c0319001573485a",
    "customerIds": [],
    "commentsFilter": {},
    "type": "Wait",
    "roles": ["5b0525134c0319001573485x", "5b0525134c0319001573485o"],
    "updatedAt": 1524056052883,
  }
}
```

## Метод изменения названия задачи
```https://botapi.workonflow.com/{teamid}/thread.title```

### Параметры:
| field         | type          | description| required|
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         |yes|
| title         | string        | новое имя задачи |yes|

### Пример тела запроса:
```json
  {
    "threadId":"5b0321234c0319001573485e",
    "title":"New title for thread"
  }
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","title":"New title for thread" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread.title```

### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```

## Метод для добавления внешних фолловеров в задачу
```https://botapi.workonflow.com/{teamid}/thread.customer/add```

### Параметры:
> **Внимание!** Одно из полей обязательно нужно передать в запросе: customerId или customerIds

| field         | type     | description| required |
| ------------- |----------| ----------------------|---:|
| threadId      | string   | индетификатор треда         | yes |
| customerId    | string   | индетификатор клиента |
| customerIds   | array    | массив индетификаторов клиентов |

### Пример тела запроса:
```json
  {
    "threadId": "5b0321234c0319001573485e",
    "customerId": "5b0321324c0319001573485e"
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","customerId": "5b0321324c0319001573484q" }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread.customer/add```

### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```

## Метод для удаления внешних фолловеров из задачи
```https://botapi.workonflow.com/{teamid}/thread.customer/remove```

### Параметры:
> **Внимание!** Одно из полей обязательно нужно передать в запросе: customerId или customerIds

| field         | type          | description| required |
| ------------- |---------------| ----------------------|--:|
| threadId      | string        | индетификатор треда         | yes |
| customerId    | string   | индетификатор клиента |
| customerIds   | array    | массив индетификаторов клиентов |

### Пример тела запроса:
```json
  {
    "threadId": "5b0321234c0319001573485e",
    "customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"]
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","customerIds": ["5b0321324c0319001573484q", "5e1451234c0319001573485e"] }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread.customer/remove```

### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```

## Метод для добавления внутренних пользователей в тред как фолловеров
```https://botapi.workonflow.com/{teamid}/thread.followers/set```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| userId        | string        | индетификатор добавляемого юзера | yes |

### Пример тела запроса:
```json
  {
    "threadId": "5b0321234c0319001573485e",
    "userId": "5b0321324c0319001573485e"
  }
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","userId": "5e1451234c0319001573485e" }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread.followers/set```

### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```

## Метод для удаления фолловеров из треда
```https://botapi.workonflow.com/{teamid}/thread.followers/remove```

### Параметры:
| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| userId        | string        | индетификатор фолловера, которого нужно удалить из треда | yes |

### Пример тела запроса:
```json
{
  "threadId": "5b0321234c0319001573485e",
  "userId": "5b0321324c0319001573485e"
}
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","userId": "5b0321324c0319001573484q" }'https://botapi.workonflow.com/333ccc134c0319001573485e/thread.followers/remove```

### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```

## Добавление тегов в тред
```https://botapi.workonflow.com/{teamid}/thread/pushtag```

> **Внимание!** На данный момент теги отображаются только на доске, где отображаются все задачи стрима. После изменения описания задачи - ТЕГ ПРОПАДЕТ.

### Параметры:
> **Внимание!** Одно из полей нужно обязательно передать в запросе: tagId или tagIds

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| tagId        | string        | индетификатор тега |  |
| tagIds        | array         | индетификаторы тегов  | |

### Пример тела запроса:
```json
{
  "threadId": "5b0321234c0319001573485e",
  "tagId": "5b0321324c0319001573485e"
}
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","tagId": "5b0321324c0319001573484q" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/pushtag```

### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```

## Удаление тегов из треда
```https://botapi.workonflow.com/{teamid}/thread/pulltag```

### Параметры:
> **Внимание!** Одно из полей нужно обязательно передать в запросе: tagId или tagIds

| field         | type          | description| required |
| ------------- |---------------| ----------------------|---:|
| threadId      | string        | индетификатор треда         | yes |
| tagId        | string        | индетификатор тега |  |
| tagIds        | array         | массив индетификаторов тегов  | |

### Пример тела запроса:
```json
{
  "threadId": "5b0321234c0319001573485e",
  "tagId": "5b0321324c0319001573485e"
}
```

### Пример запроса:
```curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0321234c0319001573485e","tagId": "5b0321324c0319001573484q" }' https://botapi.workonflow.com/333ccc134c0319001573485e/thread/pulltag```


### Пример ответа:
```json
  {"code": 200, "message": "OK"}
```
