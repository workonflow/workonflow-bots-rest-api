# Support Stream events

## Событие добавления пользователя в поток

#### Query example:
```js
  eventType: 'stream-on-user-set',
  teamId: 'team id',
  id: 'comment id',
  userId: 'user id',
  threadId: '',
  streamId: 'id stream',
  to: [],
  from: '',
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
  threadId: '',
  streamId: 'id stream',
  to: [],
  from: '',
  type: 'deleteStreamRole',
  initialUser: 'initiator user id'
```
