# Support Stream events

## Stream.deleted

**Событие стрима**
**Событие удаления потока из группы**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| streamId  | string | id of string  |
| initialUser| string | id of user, который удалил |

**Body example:**
```js
{
  eventType: 'Stream.deleted',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.created

**Событие стрима**
**Событие создания потока в группе**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| initialUser| string | id of user, который создал |

**Body example:**
```js
{
  eventType: 'Stream.created',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Updated.description

**Событие стрима**
**Событие изменения описания потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| streamId  | string | id of string  |
| initialUser| string | id of user, который создал |

**Body example:**
```js
{
  eventType: 'Stream.Updated.description',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.User.Role.remove

**Событие стрима**
**Событие удаления участника из потока группы**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| streamId  | string | id of string  |
| userId    | string | id of user, которого удалили |
| initialUser| string | id of user, который удалил |

**Body example:**
```js
{
  eventType: 'Stream.Update.User.Role.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.User.Role.set

**Событие стрима**
**Событие добавления участника в поток**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| streamId  | string | id of string  |
| userId    | string | id of user, которого добавили |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Stream.Update.User.Role.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.User.Admin.remove

**Событие стрима**
**Событие удаления админских прав у участника потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| userId    | string | id of user, у кого удалили права |
| initialUser| string | id of user, кто удалил права |

**Body example:**
```js
{
  eventType: 'Stream.Update.User.Admin.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.User.Admin.set

**Событие стрима**
**Событие добавления админских прав участнику потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| userId    | string | id of user, у кого удалили права |
| initialUser| string | id of user, кто удалил права |

**Body example:**
```js
{
  eventType: 'Stream.Update.User.Admin.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.Bot.Role.remove

**Событие стрима**
**Событие удаления бота из потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| userId    | string | id of user, которого удалили |
| initialUser| string | id of user, который удалил |

**Body example:**
```js
{
  eventType: 'Stream.Update.Bot.Role.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---

## Stream.Update.Bot.Role.set

**Событие стрима**
**Событие добавления бота в поток**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| userId    | string | id of user, которого добавили |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Stream.Update.Bot.Role.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.Bot.Admin.remove

**Событие стрима**
**Событие удаления админских прав у бота-участника потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| userId    | string | id of user, у кого удалили права |
| initialUser| string | id of user, кто удалил права |

**Body example:**
```js
{
  eventType: 'Stream.Update.Bot.Admin.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.Bot.Admin.set

**Событие стрима**
**Событие добавления админских прав боту-участнику потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| streamId  | string | id of string  |
| userId    | string | id of user, у кого удалили права |
| initialUser| string | id of user, кто удалил права |

**Body example:**
```js
{
  eventType: 'Stream.Update.Bot.Admin.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  userId: '595b405b81d3f8001497603d',
  initialUser: '5b0525134c0319001573485h'
}
```