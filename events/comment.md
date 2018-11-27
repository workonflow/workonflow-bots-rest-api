# Comment events

## Comment.created

**Событие стрима или треда**
**Событие создания коментария**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| teamId    | string | id of team    |
| eventType | string | тип события   |
| streamId  | string | id of stream, если комментарий был создан в потоке |
| threadId  | string | id of thread, если комментарий был создан в задаче |
| id        | string | id of comment |
| createdAt | number | время создания коментария в формате timestamp |
| updatedAt | number | время последнего обнавления коментария в формате timestamp |
| type      | string | Тип комментария (звонок, письмо, сообщение и т.п.) |
| to        | string | id of user получателя |
| from      | string | id of user создавший комментарий |
| att       | array  | object of transfered messages/audio/images/files |

> Пустой type означает что этот коммент - сообщение

**Body example:**

```js
{
  teamId: '595b405b81d3f8001497603d',
  eventType: 'Comment.created',
  streamId: '595b405b81d3f80014976034',
  id: '595b405b81d3f80014976031',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  type: '',
  to: '595b405b81d3f80014976032',
  from: '595b405b81d3f80014976033',
  att:  [ { "type": "text", "data": { "text": "hello world" } } ]
}
```
---

## Comment.direct

**Личное событие**
**Событие создания комментария в личном чате пользователя с ботом**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| teamId    | string | id of team    |
| eventType | string | тип события   |
| id        | string | id of comment |
| createdAt | number | время создания коментария в формате timestamp |
| updatedAt | number | время последнего обнавления коментария в формате timestamp |
| from      | string | id of user создавший комментарий |
| to        | string | id of user получившего комментарий |
| att       | array  | object of transfered messages/audio/images/files |


**Body example:**

```js
{
  eventType: 'Сomment.direct',
  teamId: '595b405b81d3f8001497603d',
  id: '595b405b81d3f80014976031',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  from: '595b405b81d3f80014976033',
  to: '595b405b81d3f800ldfgjeo3',
  att: [ { "type": "text", "data": { "text": "hello world" } } ]
}
```
---

## Comment.command

**Личное событие**
**Событие создания команды в личном чате пользователя с ботом**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| teamId    | string | id of team    |
| eventType | string | тип события   |
| id        | string | id of comment |
| createdAt | number | время создания коментария в формате timestamp |
| updatedAt | number | время последнего обнавления коментария в формате timestamp |
| from      | string | id of user создавший комментарий |
| to        | string | id of user получившего комментарий |
| att       | array  | object of transfered messages/audio/images/files |


**Body example:**

```js
{
  teamId: '595b405b81d3f8001497603d',
  eventType: 'Comment.command',
  id: '595b405b81d3f80014976031',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  from: '595b405b81d3f80014976033',
  to: '595b405b81d3f800ldfgjeo3',
  att: [ { "type": "text", "data": { "text": "hello world" } } ]
}
```
------------------------------------------------------------------------------------

## Сomment.Mention.stream

**Личное событие**
**События создания коментария с упоминанием бот-id в потоке**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| teamId    | string | id of team    |
| eventType | string | тип события   |
| streamId  | string | id of stream |
| id        | string | id of comment |
| createdAt | number | время создания коментария в формате timestamp |
| updatedAt | number | время последнего обнавления коментария в формате timestamp |
| att       | array  | object of transfered messages/audio/images/files |

**Body example:**

```js
{
  teamId: '595b405b81d3f80014976033',
  eventType: 'Сomment.Mention.stream',
  streamId: '595b405b81d3f80014976036',
  id: '595b405b81d3f80014976034',
  userId: '595b405b81d3f80014976035',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  att: [ { "type": "text", "data": { "text": "@595b405b81d3f80014976033@ hello world" } } ]
}
```
------------------------------------------------------------------------------------

## Comment.Mention.thread

**Личное событие**
**События создания коментария с упоминанием бот-id в задаче**


**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| eventType | string | тип события   |
| teamId    | string | id of team    |
| streamId  | string | id of stream |
| threadId  | string | id of thread |
| id        | string | id of comment |
| createdAt | number | время создания коментария в формате timestamp |
| updatedAt | number | время последнего обнавления коментария в формате timestamp |
| att       | array  | object of transfered messages/audio/images/files |

**Body example:**

```js
{
  teamId: '595b405b81d3f80014976033',
  eventType: 'Comment.Mention.thread',
  streamId: '595b405b81d3f80014976036',
  threadId: '595b405b81d3f80014976034',
  id: '595b405b81d3f80014976037',
  userId: '595b405b81d3f80014976036',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  att: [ { "type": "text", "data": { "text": "@595b405b81d3f80014976033@ hello world" } } ]
}
```