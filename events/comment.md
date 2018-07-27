# Comment events

## comment.created

**Событие создания коментария**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| eventType | string | тип события   | 
| teamId    | string | id of team    |
| id        | string | id of comment | 
| createdAt | number | время создания коментария в формате timestamp | 
| updatedAt | number | время последнего обнавления коментария в формате timestamp | 
| to        | string | id of user получателя |
| threadId  | string | id of thread, если комментарий был создан в задаче |
| streamId  | string | id of stream, если комментарий был создан в потоке |
| from      | string | id of user создавший комментарий | 
| attText   | string | comment text | 

**Body example:**

```js
{
  eventType: 'comment.created',
  teamId: '595b405b81d3f8001497603d',
  id: '595b405b81d3f80014976031',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  to: '595b405b81d3f80014976032',
  from: '595b405b81d3f80014976033',
  streamId: '595b405b81d3f80014976034',
  attText: 'hello world',
}
```
------------------------------------------------------------------------------------

## comment.direct

**Событие создания комментария в личном чате пользователя с ботом**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| eventType | string | тип события   | 
| teamId    | string | id of team    |
| id        | string | id of comment | 
| createdAt | number | время создания коментария в формате timestamp | 
| updatedAt | number | время последнего обнавления коментария в формате timestamp | 
| from      | string | id of user создавший комментарий | 
| attText   | string | comment text | 


**Body example:**

```js
{
  eventType: 'comment.direct',
  teamId: '595b405b81d3f8001497603d',
  id: '595b405b81d3f80014976031',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  from: '595b405b81d3f80014976033',
  attText: 'hello world',
}
```
------------------------------------------------------------------------------------

## comment.mention.stream

**События создания коментария с упоминанием бот-id в потоке**

**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| eventType | string | тип события   | 
| teamId    | string | id of team    |
| id        | string | id of comment | 
| createdAt | number | время создания коментария в формате timestamp | 
| updatedAt | number | время последнего обнавления коментария в формате timestamp | 
| streamId  | string | id of stream |
| attText   | string | comment text with botId | 

**Body example:**

```js
{
  eventType: 'comment.mention.stream',
  teamId: '595b405b81d3f80014976033',
  id: '595b405b81d3f80014976034',
  userId: '595b405b81d3f80014976035',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  attText: '@595b405b81d3f80014976033@ some text',
  streamId: '595b405b81d3f80014976036',
}
```

## comment.mention.thread

**События создания коментария с упоминанием бот-id в задаче**


**Parameters:**

| field     | type   | description  |
| --------- |--------| :----------- |
| eventType | string | тип события   | 
| teamId    | string | id of team    |
| id        | string | id of comment | 
| createdAt | number | время создания коментария в формате timestamp | 
| updatedAt | number | время последнего обнавления коментария в формате timestamp | 
| threadId  | string | id of thread |
| attText   | string | comment text | 


**Body example:**

```js
{
  eventType: 'comment.mention.stream',
  teamId: '595b405b81d3f80014976033',
  id: '595b405b81d3f80014976037',
  userId: '595b405b81d3f80014976036',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  attText: '@595b405b81d3f80014976035@ some text',
  threadId: '595b405b81d3f80014976034',
}
```