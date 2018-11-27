# Call events

## Call.created

**Событие стрима**
**Возникающее при создании звонка в стриме (Создаётся конференция, в которой может быть пусто) - участникам звонка отдельно отправляются инвайты.**

**Parameters:**

| field         | type     | description|
| --------------- |----------------|:-----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент       |
| *eventType*     |string          | Тип поступившего события                 |
| *streamId*      |string - 24 char| Id стрима, в котором произошёл звонок    |
| *threadId*      |string - 24 char| Id треда, в котором произошёл звонок     |
| *createdAt*     |number          | Timestamp, время создания звонка         |
| *originateUserId*|string         | Id пользователя, инициатора звонка       |
| *destinationId* |string          | Id пользователя, цели звонка             |
| *type*          |string          | Уточняет где был создан звонок           |

> Уникальным идентификатором звонка является *streamId* или *threadId*, Смотря где был инициирован звонок, Это видно в поле *type*

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.created',
  streamId: '5a5f27c9e0ab3e001455d10e',
  threadId: '595b405b81d3f8001497603d',
  originateUserId: '58f5ec3a32e3a300154b5e50',
  destinationId: '595b3fc381d3f8001497603c',
  type: 'thread',
  createdAt: 1539761084401
}
```
----
## Call.ended

**Событие стрима**
**Возникает при завершении звонка в стриме или треде**

**Parameters:**

| field         | type     | description|
| --------------- |----------------|:-----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент       |
| *eventType*     |string    | тип поступившего события                 |
| *streamId*      |string    | id of stream, в котором произошёл звонок |
| *threadId*      |string    | id of thread, в котором произошёл звонок |

> Поля *dialogDuration* и *callDuration* придут позже в комментарии к звонку.

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.ended',
  streamId: '5a5f27c9e0ab3e001455d10e',
  threadId: '595b405b81d3f8001497603d',
}
```
----

## Call.Member.invited

**Событие стрима**
**Событие возникает при приглашении нового участника звонка.**
***Имеется в виду начало дозвона до участника.***

**Parameters:**

| field         | type     | description|
| --------------- |----------|:----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент       |
| *eventType*     |string    | тип поступившего события                |
| *streamId*      |string    | id of stream, в котором совершён звонок |
| *threadId*      |string    | id of thread, в котором совершён звонок |
| *phone*         |string    | phone number of user                    |
| *userId*        |string    | id of user, кого призвали в конференцию |

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.Member.invited',
  streamId: '595b405b81d3f8001497603d',
  threadId: '595b405b81d3f8001497603d',
  phone: '89536052307',
  userId: '595b405b81d3f8001497603d'
}
```
---

## Call.Member.Invite.ended

**Событие стрима**
**Событие возникает в момент, когда пользователь принял/отклонил инвайт в конференцию**

**Parameters:**

| field         | type     | description|
| --------------- |----------|:----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент|
| *eventType*     |string    | тип поступившего события                |
| *streamId*      |string    | id of stream, в котором совершён звонок |
| *threadId*      |string    | id of thread, в котором совершён звонок |
| *userId*        |string    | id of user, кого призвали в конференцию |
| *phone*         |string    | phone number of user                    |
| *answered*      |boolean   | результат инвайта контакта в конференцию|


**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.Member.Invite.ended',
  threadId: '595b405b81d3f8001497603d',
  streamId: '595b405b81d3f8001497603d',
  userId: '595b405b81d3f8001497603d',
  phone: '89536052307',
  answered: true
}
```
----

## Call.Member.leaved

**Событие стрима**
**Событие возникает при удалении участника звонка**

**Parameters:**

| field         | type     | description|
| --------------- |----------|:----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент|
| *eventType*     |string    | тип поступившего события                |
| *threadId*      |string    | id of thread, в котором совершён звонок |
| *streamId*      |string    | id of stream, в котором совершён звонок |
| *phone*         |string    | phone number of user                    |
| *userId*        |string    | id of user, кого удалили из конференции |

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.Member.leaved',
  streamId: '595b405b81d3f8001497603d',
  threadId: '595b405b81d3f8001497603d',
  phone: '89536052307',
  userId: '595b405b81d3f8001497603d'
}
```
----

## Call.Member.held

**Событие стрима**
**Событие поступает когда участник звонка был поставлен на паузу**

**Parameters:**

| field         | type     | description|
| --------------- |----------|:-----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент|
| *eventType*     |string    | тип поступившего события                 |
| *streamId*      |string    | id of stream, в котором совершён звонок  |
| *threadId*      |string    | id of thread, в котором совершён звонок  |
| *phone*         |string    | phone number of user                     |
| *userId*        |string    | id of user, кого поставили на паузу      |

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.Member.held',
  streamId: '595b405b81d3f8001497603d',
  threadId: '595b405b81d3f8001497603d',
  phone: '89536052307',
  userId: '595b405b81d3f8001497603d'
}
```
----

## Call.Member.unheld

**Событие стрима**
**Событие поступает когда участник звонка был снят с паузы**

**Parameters:**

| field         | type     | description|
| --------------- |----------|:-----------------------------------------|
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент|
| *eventType*     |string    | тип поступившего события                 |
| *streamId*      |string    | id of stream, в котором совершён звонок  |
| *threadId*      |string    | id of thread, в котором совершён звонок  |
| *phone*         |string    | phone number of user                     |
| *userId*        |string    | id of user, кого сняли с паузы           |

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.Member.unheld',
  streamId: '595b405b81d3f8001497603d',
  threadId: '595b405b81d3f8001497603d',
  phone: '89536052307',
  userId: '595b405b81d3f8001497603d'
}
```
----

## Call.Member.dtmf

**Событие стрима**
**Событие возникает при срабатывании [DTMF](https://ru.wikipedia.org/wiki/DTMF) набора одним из участников**

**Parameters:**

| field         | type     | description|
| --------------- |----------|:----------------------                   |
| *teamId*        |string - 24 char| Id тимы, в котором произошёл ивент |
| *eventType*     |string    | тип поступившего события                 |
| *streamId*      |string    | id of stream, в котором совершён звонок  |
| *threadId*      |string    | id of thread, в котором совершён звонок  |
| *dtmfNumber*    |number    | переданный DTMF сигнал                   |
| *phone*         |string    | phone number of user                     |
| *userId*        |string    | id of user, набравшего dtmf              |

**Body example:**
```js
{
  teamId: '545b508981d3f8001497d03d',
  eventType: 'Call.Member.dtmf',
  streamId: '595b405b81d3f8001497603d',
  threadId: '595b405b81d3f8001497603d',
  dtmfNumber: '1',
  phone: '89536052307',
  userId: '595b405b81d3f8001497603d'  
}
```
