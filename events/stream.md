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

## Stream.user.set

**Событие добавления пользователя в поток**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого добавили в поток |
| streamId  | string | id of string  |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Stream.user.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
--------------------------------------------------------------------------------

## Stream.user.deleted

**Событие удаления пользователя из потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого удалили из потока |
| streamId  | string | id of string  |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Stream.user.deleted',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.bot.set

**Событие добавления бота в поток**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| botid     | string | id of bot, которого добавили |
| streamId  | string | id of string  |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Stream.bot.set',
  teamId: '5b0525134c0319001573485e',
  botId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## Stream.bot.deleted

**Событие удаления бота из потока**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого удалили из потока |
| streamId  | string | id of string  |
| initialUser| string | id of user, который добавил |


**Body example:**
```js
{
  eventType: 'Stream.bot.deleted',
  teamId: '5b0525134c0319001573485e',
  botId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```