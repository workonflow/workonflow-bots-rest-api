# Tema events

## team.admin.status.give

**Событие получения пользователем прав администратора**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user    |

**Body example:**

```js
{
  eventType: 'team.admin.status.give',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f'
}
```
-------------------------------------------

## team.admin.status.revoked

**Событие изъятия у пользователем прав администратора**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user    |

**Body example:**

```js
{
  eventType: 'team.admin.status.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f' 
}
```
----------------

## team.user.invited

**Событие приглашения пользователя в "тиму"**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user    |
| email     | string | user email    |
**Body example:**

```js
{
  eventType: 'team.user.invited',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f' 
  email: 'example@gmail.com'
}
```
----------------------------------------------

## team.user.removed

**Событие удаления пользователя из "тимы"**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user    |

**Body example:**

```js
{
  eventType: 'team.user.removed',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f' 
}
  teamId: 'team id',
  userId: 'user id'
```
-------------------------

## team.bot.invited

**Событие приглашения бота в "тиму"**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user    |

**Body example:**

```js
{
  eventType: 'team.bot.invited',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f' 
}
```
------------------

## team.bot.removed

**Событие удаления бота из "тимы"**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user    |

**Body example:**

```js
{
  eventType: 'team.bot.removed',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f' 
}
```
