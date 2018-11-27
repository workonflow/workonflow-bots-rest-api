# Team events

## Admin.User.set

**Событие тимы**
**Событие получения пользователем прав администратора**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которому дали доступ |
| initialUser| string | id of user, который дал доступ |
| isAdmin    | boolean| is admin or not    |
| billingType| string | bot/user/client    |
| email     | string | user email    |

**Body example:**

```js
{
  eventType: 'Admin.User.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  initialUser: '5b0525134c0319001573485h',
  email: 'example@gmail.com',
  billingType: 'bots',
  isAdmin: true  
}
```
-------------------------------------------

## Admin.User.revoked

**Событие тимы**
**Событие изъятия у пользователем прав администратора**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которому дали доступ |
| profileId    | string | global id of bot    |
| initialUser| string | id of user, который дал доступ |
| email     | string | user email    |

**Body example:**

```js
{
  eventType: 'Admin.User.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  profileId: '58f5ec3a32e3a300154b5e50',
  initialUser: '5b0525134c0319001573485h',
  email: 'example@gmail.com'
}
```
----------------

## Access.User.set

**Событие тимы**
**Событие приглашения пользователя в группу**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| userId    | string | id of user, которому дали доступ |
| initialUser| string | id of user, который дал доступ |
| billingType| string | bot/user/client    |
| isAdmin    | boolean| is admin or not    |
| email     | string | user email    |

**Body example:**

```js
{
  eventType: 'Access.User.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  email: 'example@gmail.com',
  initialUser: '5b0525134c0319001573485h',
  billingType: 'users',
  isAdmin: true
}
```
----------------------------------------------

## Access.User.revoked

**Событие тимы**
**Событие удаления пользователя из группы**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| profileId    | string | global id of user    |
| userId    | string | id of user, которому дали доступ |
| initialUser| string | id of user, который дал доступ |
| email     | string | user email    |

**Body example:**

```js
{
  eventType: 'Access.User.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  initialUser: '5b0525134c0319001573485h',
  profileId: '58f5ec3a32e3a300154b5e50',
  email: 'example@gmail.com',
}
```
-------------------------

## Access.Bot.set

**Событие тимы**
**Событие приглашения бота в группу**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| teamId    | string | id of team    |
| eventType | string | type of event |
| userId    | string | id of bot, которому дали доступ |
| initialUser| string | id of bot, который дал доступ |
| billingType| string | bot/user/client    |
| isAdmin    | boolean| is admin or not    |
| email     | string | bot email    |

**Body example:**

```js
{
  eventType: 'Access.Bot.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  email: 'example@gmail.com',
  initialUser: '5b0525134c0319001573485h',
  billingType: 'bots'
  isAdmin: true
}
```
------------------

## Access.Bot.revoked

**Событие тимы**
**Событие удаления бота из группы**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| profileId    | string | global id of bot    |
| userId    | string | id of bot, которому дали доступ |
| initialUser| string | id of user, который дал доступ |
| email     | string | bot email    |

**Body example:**

```js
{
  eventType: 'Access.Bot.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  initialUser: '5b0525134c0319001573485h',
  profileId: '58f5ec3a32e3a300154b5e50',
  email: 'example@gmail.com',
}
```
---

## Admin.Bot.set

**Событие тимы**
**Событие получения ботом прав администратора**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of bot, которому дали доступ |
| initialUser| string | id of bot, который дал доступ |
| isAdmin    | boolean| is admin or not    |
| billingType| string | bot/user/client    |
| email     | string | bot email    |

**Body example:**

```js
{
  eventType: 'Admin.Bot.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  initialUser: '5b0525134c0319001573485h',
  email: 'example@gmail.com',
  billingType: 'bots',
  isAdmin: true  
}
```
-------------------------------------------

## Admin.Bot.revoked

**Событие тимы**
**Событие изъятия у бота прав администратора**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of bot, которому дали доступ |
| profileId    | string | global id of bot    |
| initialUser| string | id of bot, который дал доступ |
| email     | string | bot email    |

**Body example:**

```js
{
  eventType: 'Admin.Bot.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573485f',
  profileId: '58f5ec3a32e3a300154b5e50',
  initialUser: '5b0525134c0319001573485h',
  email: 'example@gmail.com'
}
```