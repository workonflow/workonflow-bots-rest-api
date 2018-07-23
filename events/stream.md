# Support Stream events

## Событие добавления пользователя в поток

#### Query example:
```js
  eventType: 'stream-on-user-set',
  teamId: 'team id',
  id: 'comment id',
  userId: 'user id',
  streamId: 'id stream',
  type: 'setStreamRole',
  initialUser: 'initiator user id'
```

## Событие удаления пользователя из потока

#### Query example:
```js
  eventType: 'stream-on-user-deleted',
  teamId: 'team id',
  id: 'comment id',
  userId: 'user id',
  streamId: 'id stream',
  type: 'deleteStreamRole',
  initialUser: 'initiator user id'
```

## Событие добавления бота в поток

#### Query example:
```js
  eventType: 'stream-on-bot-set',
  teamId: 'team id',
  id: 'comment id',
  userId: 'user id',
  streamId: 'id stream',
  type: 'setStreamRole',
  initialUser: 'initiator user id'
```

## Событие удаления бота из потока

#### Query example:
```js
  eventType: 'stream-on-bot-deleted',
  teamId: 'team id',
  id: 'comment id',
  userId: 'user id',
  streamId: 'id stream',
  type: 'deleteStreamRole',
  initialUser: 'initiator user id'
```

