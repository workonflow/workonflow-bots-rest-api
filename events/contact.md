## Auth.access.invited

**Событие добавления пользователя в команду**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого добавили в поток |
| email     | string | users email  |
| billingType| string | (bots or users)  |
| isAdmin| string | user is admin or not  |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'stream.user.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com',
  billingType: 'bots',
  isAdmin: false
}
```
--------------------------------------------------------------------------------

## Auth.access.revoked

**Событие удаления пользователя из команды**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId    | string | id of user, которого удалили из потока |
| profileId | string | id of user, глобальный id юзера |
| email     | string | string  |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Auth.access.revoked',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  profileId: '5b323888e0a614001eecf8da',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com'
}
```
---------------------------------------------------------------------------------

## Auth.admin.given

**Событие добавления прав администратора пользователю**

**Parameters:**

| field     | type   | description   |
| --------- | ------ | ------------  |
| eventType | string | type of event |
| teamId    | string | id of team    |
| userId     | string | id of user, которого добавили |
| initialUser| string | id of user, который добавил |

**Body example:**
```js
{
  eventType: 'Auth.admin.given',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
---------------------------------------------------------------------------------

## Auth.admin.revoked

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
  eventType: 'Auth.admin.given',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
---------------------------------------------------------------------------------