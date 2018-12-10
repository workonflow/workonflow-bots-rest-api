# Team requests

## Метод для приглашения пользователя в систему workonflow
```https://botapi.workonflow.com/{teamId}/invite.user```

### Параметры:
| field    | type   | description| required |
| -------- |--------| :----------------------|---:|
| name     | string | имя юзера   | yes |
| email    | string | эл. почта юзера | yes |

## Пример тела запроса:
```json
  {
    "name": "Jon Si",
    "email": "jon@www.com"
  }
```

## Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "name":"Jon Si", "email": "jon@www.com" }' https://botapi.workonflow.com/333ccc134c0319001573485e/invite.user```

## Пример ответа:
```json
 { "code": 200, "message": "OK" }
```
