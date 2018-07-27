# Team requests

## team/invite.user

**Метод для приглашения пользователя в систему workonflow**

```js
  api.workonflow.com/{teamId}/team/invite.user/{query}
```
**Parameters:**

| field    | type   | description|
| -------- |--------| :----------------------|
| name     | string | new name for stream   |
| email    | string | user name |

**Query params example:**

```json
{
  "query":{
    "name": "Jon Si",
    "email": "true"
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "name":"New stream" }}' https://api.workonflow.com/333ccc134c0319001573485e/team/invite.user
```

**Response example:**
```js
 { code: 200, message: 'OK' }
```