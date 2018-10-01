## Contact.Access.user.set

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
  eventType: 'Contact.Access.user.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com',
  billingType: 'bots',
  isAdmin: false
}
```
--------------------------------------------------------------------------------

## Contact.Access.user.remove

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
  eventType: 'Contact.Access.user.remove',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  profileId: '5b323888e0a614001eecf8da',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com'
}
```
---------------------------------------------------------------------------------

## Contact.Admin.user.set

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
  eventType: 'Contact.Admin.user.set',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
---------------------------------------------------------------------------------

## Contact.Admin.user.remove

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
  eventType: 'Contact.Admin.user.remove',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
## Contact.Access.bot.set

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
  eventType: 'Contact.Access.bot.set',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com',
  billingType: 'bots',
  isAdmin: false
}
```
--------------------------------------------------------------------------------

## Contact.Access.bot.remove

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
  eventType: 'Contact.Access.bot.remove',
  teamId: '5b0525134c0319001573485e',
  userId: '5b71621d444507001b8be440',
  profileId: '5b323888e0a614001eecf8da',
  initialUser: '5b0525134c0319001573485h',
  email: 'testVit@workonflow.com'
}
```
---------------------------------------------------------------------------------

## Contact.Admin.bot.set

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
  eventType: 'Contact.Admin.bot.set',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```
---------------------------------------------------------------------------------

## Contact.Admin.bot.remove

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
  eventType: 'Contact.Admin.bot.remove',
  teamId: '5b0525134c0319001573485e',
  initialUser: '5b0525134c0319001573485h',
  userId: '5b6ace2b344508001b8be434'
}
```