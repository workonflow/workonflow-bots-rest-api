# Call events

### call.started

**Событие поступает при создании звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------|
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call|
| threadId      |string    | id of thread, в котором произошёл звонок |

**Body example:**
```js
{
  eventType: 'call.started',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
}
```
----
### call.ended

**Событие поступает при завершении звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------|
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call             |
| threadId      |string    | id of thread, в котором произошёл звонок |
| dialogDuration|number    | длительность разговора в милисекундах |
| callDuration  |number    | длительность звонка в милисекундах |

**Body example:**
```js
{
  eventType: 'call.ended',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  dialogDuration: 5554,
  callDuration: 5599
}
```
----

### call.user.invited

**Событие поступает при приглашении участника звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------|
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call|
| threadId      |string    | id of thread, в котором произошёл звонок |
| contactId     |string    | id of user|

**Body example:**
```js
{
  eventType: 'call.user.invited',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  contactId: '595b405b81d3f8001497603d'
}
```
----

### call.user.removed

**Событие поступает при удалении участника звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------|
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call|
| threadId      |string    | id of thread, в котором произошёл звонок |
| contactId     |string    | id of user|

**Body example:**
```js
{
  eventType: 'call.user.removed',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f',
  contactId: '595b405b81d3f8001497603d'
}
```
----

### call.on.paused

**Событие поступает когда звонк был поставлен на паузу**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------|
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call|
| threadId      |string    | id of thread, в котором произошёл звонок |

**Body example:**
```js
{
  eventType: 'call.on.paused',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
}
```
----

### call.off.paused

**Событие поступает когда звонок был снят с паузы**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------|
| eventType     |string    | тип поступившего события |
| callId        |string    | id of call|
| threadId      |string    | id of thread, в котором произошёл звонок |

**Body example:**
```js
{
  eventType: 'call.off.paused',
  threadId: '595b405b81d3f8001497603d',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
}
```
----

### call.emit.dtmf

**Событие поступает при срабатывание [DTMF](https://ru.wikipedia.org/wiki/DTMF) набора**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------   |
| eventType     |string    | тип поступившего события |
| dtmfNumber    |number    | переданный DTMF сигнал   |

**Body example:**
```js
{
  eventType: 'call.off.paused',
  threadId: '595b405b81d3f8001497603d',
  dtmfNumber: '1',
  callId: '522a2f93-4463-4040-8176-947b2c77bd0f'
}
```
