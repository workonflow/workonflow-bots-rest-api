# Thread events

## Thread.created

**Событие стрима**
**Событие создания треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id of stream  |
| title     | string | thread title  |
| responsibleUserId|string| id of user, ответственный за задачу |
| userId    | string | id of user, который создал задачу |

**Body example:**
```js
{
  eventType: 'Thread.created',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485v',
  title: 'new thread',
  responsibleUserId: '5b0525134c0319001573485b',
  userId: '5b0525134c0319001573485x'
}
```
-------------------------------
## Thread.updated

**Событие стрима**
**Событие изменения треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| threadId  | string | id of thread  |
| streamId  | string | id of stream  |
| userId    | string | id of user, который создал задачу |
| fieldName | string | название поля которое было изменено |
| fieldPayload|string| новое значение поля |

**Body example:**
```js
{
  eventType: 'Thread.updated',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485v',
  userId: '5b0525134c0319001573485x',
  fieldName: "points",
  fieldPayload: "40"
}
```
-------------------------------
## Thread.Updated.status

**Событие стрима**
**Событие смены статуса треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id of stream  |
| userId    | string | id of user, который создал задачу |
| statusId  | string | id нового статуса |
| previousStatusId|string| id предыдущего статуса |

**Body example:**
```js
{
  eventType: 'Thread.Updated.status',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485v',
  userId: '5b0525134c0319001573485x',
  statusId: "5b0525134c03190015734new",
  prevStatusId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.stream

**Событие стрима**
**Событие смены стрима, в котором находится тред**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| userId    | string | id of user, который создал задачу |
| streamId  | string | id новой тимы |
| prevStreamId|string| id предыдущей тимы |

**Body example:**
```js
{
  eventType: 'Thread.Updated.stream',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734new",
  prevStreamId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.Customer.set

**Событие стрима**
**Событие добавления кастомера (клиента) в тред**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| customerId|string| id клиента |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Customer.set',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734cnj",
  customerId: "5b0525134c0319001573weft"
}
```
-------------------------------
## Thread.Updated.Customer.remove

**Событие стрима**
**Событие удаления кастомера (клиента) из треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id od stream |
| userId    | string | id of user, который удалил клиента из треда |
| customerId|string| id клиента |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Customer.remove',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734fgkm",
  customerId: "5b0525134c0319001573ldsbf"
}
```
-------------------------------
## Thread.Updated.Follower.set

**Событие стрима**
**Событие добавления сотрудника в тред**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| roleId    | string | id сотрудника |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Follower.set',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734g0j",
  roleId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.Follower.remove

**Событие стрима**
**Событие удаления сотрудника из треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| roleId    | string | id сотрудника |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Follower.remove',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  roleId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.Bot.Follower.set

**Событие стрима**
**Событие добавления бота в тред**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| roleId    | string | id бота |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Bot.Follower.set',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  roleId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.Bot.Follower.remove

**Событие стрима**
**Событие удаления бота из треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| roleId    | string | id бота |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Bot.Follower.remove',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  roleId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.Responsible.set

**Событие стрима**
**Событие добавления (или смены) ответственного сотрудника в тред**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| responsibleUserId| string | id ответственного сотрудника |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Responsible.set',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  responsibleUserId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.Responsible.remove

**Событие стрима**
**Событие удаления ответственного сотрудника из треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| responsibleUserId| string | id ответственного сотрудника |

**Body example:**
```js
{
  eventType: 'Thread.Updated.Responsible.remove',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  responsibleUserId: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.budget

**Событие стрима**
**Событие изменения бюджета треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| budget    | integer | сумма бюджета сделки |

**Body example:**
```js
{
  eventType: 'Thread.Updated.budget',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  budget: "5b0525134c0319001573last"
}
```
-------------------------------
## Thread.Updated.deadline

**Событие стрима**
**Событие изменения дедлайна треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| deadline  | array  | Дата дедлайна (Или период с даты по дату) |

**Body example:**
```js
{
  eventType: 'Thread.Updated.deadline',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  deadline: "[null, 1538118000000]"
}
```
-------------------------------
## Thread.Updated.points

**Событие стрима**
**Событие изменения очков важности треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| mainRank  | integer  | Оценка сложности задачи |

**Body example:**
```js
{
  eventType: 'Thread.Updated.points',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  mainRank: 5
}
```
-------------------------------
## Thread.Updated.priority

**Событие стрима**
**Событие изменения очков приоритета треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| priority  | string  | Приоритет  |

**Body example:**
```js
{
  eventType: 'Thread.Updated.priority',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  priority: "High"
}
```
-------------------------------
## Thread.Updated.toc

**Событие стрима**
**Событие изменения времени очков времени выполнения треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| resource  | integer | ресурс времени  |

**Body example:**
```js
{
  eventType: 'Thread.Updated.toc',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  resource: 20
}
```
-------------------------------
## Thread.Updated.title

**Событие стрима**
**Событие изменения заголовка треда**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| threadId  | string | id of thread  |
| streamId  | string | id новогй тимы |
| userId    | string | id of user, который добавил клиента в тред |
| title     | string | текст заголовка  |

**Body example:**
```js
{
  eventType: 'Thread.Updated.title',
  teamId: '5b0525134c0319001573485e',
  threadId: '5b0525134c0319001573485f',
  userId: '5b0525134c0319001573485x',
  streamId: "5b0525134c03190015734yd5",
  title: 'best Thread ever!'
}
```