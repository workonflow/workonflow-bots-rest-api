# Team requests

## team/invite.user

**Метод для приглашения пользователя в систему workonflow**

```js
  https://botapi.workonflow.com/{teamId}/invite.user/{body}
```
**Parameters:**

| field    | type   | description| required |
| -------- |--------| :----------------------|---:|
| name     | string | User name   | yes |
| email    | string | Email of user | yes |

**Body message example:**
```json
  {
    "name": "Jon Si",
    "email": "jon@www.com"
  }
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "name":"Jon Si", "email": "jon@www.com" }' https://botapi.workonflow.com/333ccc134c0319001573485e/invite.user
```

**Response example:**
```js
 { code: 200, message: 'OK' }
```
