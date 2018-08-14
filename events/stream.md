# Support Stream events

## stream.user.set

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
  eventType: 'stream.user.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
--------------------------------------------------------------------------------

## stream.user.deleted

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
  eventType: 'stream.user.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## stream.bot.set

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
  eventType: 'stream.bot.set',
  teamId: '5b0525134c0319001573485e',
  botId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## stream.bot.deleted

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
  eventType: 'stream.bot.deleted',
  teamId: '5b0525134c0319001573485e',
  botId: '5b0525134c0319001573485f',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------

## stream.deleted

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
  eventType: 'stream.user.set',
  teamId: '5b0525134c0319001573485e',
  streamId: '5b0525134c0319001573485d',
  initialUser: '5b0525134c0319001573485h'
}
```
---------------------------------------------------------------------------------