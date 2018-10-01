# Support Stream events

---------------------------------------------------------------------------------

## Stream.deleted

**Событие удаления потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
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

**Событие создания потока**

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

## Stream.Update.description

**Событие изменения описания потока**

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
  eventType: 'Stream.Update.description',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.user.role.remove

**Событие удаления участника из потока**

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
  eventType: 'Stream.Update.user.role.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.user.role.set

**Событие добавления участника в поток**

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
  eventType: 'Stream.Update.user.role.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.user.admin.remove

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
  eventType: 'Stream.Update.user.admin.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.user.admin.set

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
  eventType: 'Stream.Update.user.admin.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.bot.role.remove

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
  eventType: 'Stream.Update.bot.role.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.bot.role.set

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
  eventType: 'Stream.Update.bot.role.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.bot.admin.remove

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
  eventType: 'Stream.Update.bot.admin.remove',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.Update.bot.admin.set

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
  eventType: 'Stream.Update.bot.admin.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```