## Access.User.set

**Событие добавления пользователя в команду**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого добавили в поток |
| initialUser| string | id of user, который добавил |
| email     | string | users email  |
| billingType| string | (bots or users)  |
| isAdmin| string | user is admin or not  |

**Body example:**
```js
{
  eventType: 'Access.User.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com',
  billingType: 'bots',
  isAdmin: false
}
```
--------------------------------------------------------------------------------

## Access.User.revoked

**Событие удаления пользователя из команды**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого удалили из потока |
| profileId | string | id of user, глобальный id юзера |
| initialUser| string | id of user, который добавил |
| email     | string | string  |

**Body example:**
```js
{
  eventType: 'Access.User.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  profileId: '5b323888e0a614001eecf8da',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com'
}
```
---------------------------------------------------------------------------------

## Admin.User.set

**Событие добавления прав администратора пользователю**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| initialUser| string | id of user, который добавил |
| userId     | string | id of user, которого добавили |

**Body example:**
```js
{
  eventType: 'Admin.User.set',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
---------------------------------------------------------------------------------

## Admin.User.revoked

**Событие выключения прав администратора пользователю**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, у которого удалили права |
| initialUser| string | id of user, который удалил права |


**Body example:**
```js
{
  eventType: 'Admin.User.revoked',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
## Access.Bot.set

**Событие добавления бота в команду**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого добавили в поток |
| initialUser| string | id of user, который добавил |
| email     | string | users email  |
| billingType| string | (bots or users)  |
| isAdmin| string | user is admin or not  |

**Body example:**
```js
{
  eventType: 'Access.Bot.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com',
  billingType: 'bots',
  isAdmin: false
}
```
--------------------------------------------------------------------------------

## Access.Bot.revoked

**Событие удаления бота из команды**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого удалили из потока |
| profileId | string | id of user, глобальный id юзера |
| initialUser| string | id of user, который добавил |
| email     | string | string  |

**Body example:**
```js
{
  eventType: 'Access.Bot.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  profileId: '5b323888e0a614001eecf8da',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com'
}
```
---------------------------------------------------------------------------------

## Admin.Bot.set

**Событие добавления прав администратора боту**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| initialUser| string | id of user, который добавил |
| userId     | string | id of user, которого добавили |

**Body example:**
```js
{
  eventType: 'Admin.Bot.set',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
---------------------------------------------------------------------------------

## Admin.Bot.revoked

**Событие выключения прав администратора боту**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, у которого удалили права |
| initialUser| string | id of user, который удалил права |


**Body example:**
```js
{
  eventType: 'Admin.Bot.revoked',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```