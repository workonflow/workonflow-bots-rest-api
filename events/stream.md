# Support Stream events

## Событие добавления пользователя в поток

#### Query example:
```js
  { 
    eventType: 'stream-on-user-set',
    teamId: 'team id',
    data: {
      id: 'comment id',
      userId: 'user id',
      threadId: '',
      streamId: 'id stream',
      to: [],
      from: '',
      type: 'setStreamRole',
      metadata: {
        userId: 'user id',
        user: 'initiator user id'
      },
      att: []
    },
  }
```

## Событие удаления пользователя из потока

#### Query example:
```js
  { 
    eventType: 'stream-on-user-deleted',
    teamId: 'team id',
    data: {
      id: 'comment id',
      userId: 'user id',
      threadId: '',
      streamId: 'id stream',
      to: [],
      from: '',
      type: 'deleteStreamRole',
      metadata: {
        userId: 'user id',
        user: 'initiator user id'
      },
      att: []
    },
  }
```
