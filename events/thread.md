# Thread events

## thread.created

**Событие создания треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, который создал задачу |
| threadId  | string | id of thread  |
| streamId  | string | id of stream  |
| title     | string | thread title  |
| responsibleUserId|string| id of user, ответственный за задачу |

**Body example:**
```js
{
  eventType: 'thread-on-created',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485v',
  title: 'new thread',
  responsibleUserId: '5b0525134c0319001573485b',
  userId: '5b0525134c0319001573485x'
}
```
-------------------------------
**Событие изменения треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, который создал задачу |
| threadId  | string | id of thread  |
| streamId  | string | id of stream  |
| fieldName | string | название поля которое было изменено |
| fieldPayload|string| новое значение поля |

**Body example:**
```js
{
  eventType: 'thread-on-created',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485v',
  userId: '5b0525134c0319001573485x'
  fieldName: "points",
  fieldPayload: "40"
}
```