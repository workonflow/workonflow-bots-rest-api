# Support Tema events

## Событие получения пользователем прав администратора

#### Query example:
```js
  { 
    eventType: 'team-on-admin-status-give',
    teamId: 'team id',
    data: { userId: 'user id' }
  }
```

## Событие изъятия у пользователем прав администратора

#### Query example:
```js
  { 
    eventType: 'team-on-admin-status-revoked',
    teamId: 'team id',
    data: { userId: 'user id' }
  }
```

## Событие приглашения пользователя в "тиму"

#### Query example:
```js
  { 
    eventType: 'team-on-user-invited',
    teamId: 'team id',
    data: {
      userId: 'user id',
      email: 'user email'
    }
  }
```

## Событие удаления пользователя из "тимы"

#### Query example:
```js
  { 
    eventType: 'team-on-user-removed',
    teamId: 'team id',
    data: { userId: 'user id' }
  }
```