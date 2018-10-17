# Call events

### call.created

**Событие возникающее при создании звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| callId        |string    | id of call                               |
| threadId      |string    | id of thread, в котором произошёл звонок |
| streamId      |string    | id of stream, в котором произошёл звонок |
| createdAt     |number    | timestamp, время создания звонка         |

**Body example:**
```js
{
  eventType: 'call.created',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  threadId: '595b405b81d3f8001497603d',
  streamId: '5a5f27c9e0ab3e001455d10e',
  createdAt: 1539761084401
}
```
----
### call.ended

**Событие возникает при завершении звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| callId        |string    | id of call                               |
| threadId      |string    | id of thread, в котором произошёл звонок |
| streamId      |string    | id of stream, в котором произошёл звонок |
| dialogDuration|number    | длительность разговора в милисекундах    |
| callDuration  |number    | длительность звонка в милисекундах       |

**Body example:**
```js
{
  eventType: 'call.ended',
  streamId: '5a5f27c9e0ab3e001455d10e',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  dialogDuration: 5554,
  callDuration: 5599
}
```
----

### call.user.invited

**Событие возникает при приглашении нового участника звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------------------------|
| eventType     |string    | тип поступившего события                |
| callId        |string    | id of call                              |
| threadId      |string    | id of thread, в котором совершён звонок |
| streamId      |string    | id of stream, в котором совершён звонок |
| userId        |string    | id of user, кого призвали в конференцию |

**Body example:**
```js
{
  eventType: 'call.user.invited',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  userId: '595b405b81d3f8001497603d'
}
```
----

### call.user.removed

**Событие возникает при удалении участника звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------------------------|
| eventType     |string    | тип поступившего события                |
| callId        |string    | id of call                              |
| threadId      |string    | id of thread, в котором совершён звонок |
| streamId      |string    | id of stream, в котором совершён звонок |
| userId        |string    | id of user, кого удалили из конференции |

**Body example:**
```js
{
  eventType: 'call.user.removed',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  userId: '595b405b81d3f8001497603d'
}
```
----

### call.user.paused

**Событие поступает когда участник звонка был поставлен на паузу**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| callId        |string    | id of call                               |
| threadId      |string    | id of thread, в котором совершён звонок  |
| streamId      |string    | id of stream, в котором совершён звонок  |
| userId        |string    | id of user, кого поставили на паузу      |

**Body example:**
```js
{
  eventType: 'call.user.paused',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  userId: '595b405b81d3f8001497603d'
}
```
----

### call.user.unpaused

**Событие поступает когда участник звонка был снят с паузы**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| callId        |string    | id of call                               |
| threadId      |string    | id of thread, в котором совершён звонок  |
| streamId      |string    | id of stream, в котором совершён звонок  |
| userId        |string    | id of user, кого сняли с паузы           |

**Body example:**
```js
{
  eventType: 'call.user.unpaused',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  userId: '595b405b81d3f8001497603d'
}
```
----

### call.dtmf

**Событие возникает при срабатывании [DTMF](https://ru.wikipedia.org/wiki/DTMF) набора**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------   |
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call                               |
| threadId      |string    | id of thread, в котором совершён звонок  |
| streamId      |string    | id of stream, в котором совершён звонок  |
| dtmfNumber    |number    | переданный DTMF сигнал   |

**Body example:**
```js
{
  eventType: 'call.dtmf',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  dtmf: '1',
}
