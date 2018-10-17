# Call events

### call.created

**Событие возникающее при создании звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| threadId      |string    | id of thread, в котором произошёл звонок |
| streamId      |string    | id of stream, в котором произошёл звонок |
| createdAt     |number    | timestamp, время создания звонка         |

**Body example:**
```js
{
  eventType: 'call.created',
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
| threadId      |string    | id of thread, в котором произошёл звонок |
| streamId      |string    | id of stream, в котором произошёл звонок |

/* Поля dialogDuration  и callDuration придут позже в комментарии к звонку. */

**Body example:**
```js
{
  eventType: 'call.ended',
  streamId: '5a5f27c9e0ab3e001455d10e',
  threadId: '595b405b81d3f8001497603d',
}
```
----

### call.user.invited

**Событие возникает при приглашении нового участника звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------------------------|
| eventType     |string    | тип поступившего события                |
| phoneNumber   |string    | phone number of user                    |
| threadId      |string    | id of thread, в котором совершён звонок |
| streamId      |string    | id of stream, в котором совершён звонок |
| contactId     |string    | id of user, кого призвали в конференцию |

**Body example:**
```js
{
  eventType: 'call.user.invited',
  phoneNumber: '89536052307',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  contactId: '595b405b81d3f8001497603d'
}
```
----

### call.user.kicked

**Событие возникает при удалении участника звонка**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------------------------|
| eventType     |string    | тип поступившего события                |
| phoneNumber   |string    | phone number of user                    |
| threadId      |string    | id of thread, в котором совершён звонок |
| streamId      |string    | id of stream, в котором совершён звонок |
| contactId     |string    | id of user, кого удалили из конференции |

**Body example:**
```js
{
  eventType: 'call.user.kicked',
  phoneNumber: '89536052307',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  contactId: '595b405b81d3f8001497603d'
}
```
----

### call.user.held

**Событие поступает когда участник звонка был поставлен на паузу**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| phoneNumber   |string    | phone number of user                     |
| threadId      |string    | id of thread, в котором совершён звонок  |
| streamId      |string    | id of stream, в котором совершён звонок  |
| contactId     |string    | id of user, кого поставили на паузу      |

**Body example:**
```js
{
  eventType: 'call.user.held',
  phoneNumber: '89536052307',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  contactId: '595b405b81d3f8001497603d'
}
```
----

### call.user.unheld

**Событие поступает когда участник звонка был снят с паузы**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:-----------------------------------------|
| eventType     |string    | тип поступившего события                 |
| phoneNumber   |string    | phone number of user                     |
| threadId      |string    | id of thread, в котором совершён звонок  |
| streamId      |string    | id of stream, в котором совершён звонок  |
| contactId     |string    | id of user, кого сняли с паузы           |

**Body example:**
```js
{
  eventType: 'call.user.unheld',
  phoneNumber: '89536052307',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  contactId: '595b405b81d3f8001497603d'
}
```
----

### call.dtmf

**Событие возникает при срабатывании [DTMF](https://ru.wikipedia.org/wiki/DTMF) набора**

**Parameters:**

| field         | type     | description|
| ------------- |----------|:----------------------   |
| eventType     |string    | тип поступившего события |
| threadId      |string    | id of thread, в котором совершён звонок  |
| streamId      |string    | id of stream, в котором совершён звонок  |
| dtmfNumber    |number    | переданный DTMF сигнал   |

**Body example:**
```js
{
  eventType: 'call.dtmf',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  dtmf: '1',
}
```
