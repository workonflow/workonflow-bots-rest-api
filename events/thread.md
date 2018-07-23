# Support Thread events

## Событие создания треда

#### Query example:
```js
  {
    eventType: 'thread-on-created',
    teamId: 'team id',
    data: {
      threadId: 'thread id',
      streamId: 'stream id',
      type: 'create',
      metadata: {
        title: '',
        responsibleUserId: '',
        userId: 'id user creator'
      },
      att: []
    },
  }
```

## Событие обновления статуса треда

#### Query example:
```js
  {
    eventType: 'thread-on-status-update',
    teamId: 'team id',
    data: {
      threadId: 'thread id',
      streamId: 'stream id',
      to: [],
      from: '',
      type: 'setStatus',
      metadata: {
        userId: 'id user initiator',
        statusId: 'status id',
        prevStatusId: 'status id'
      },
      att: []
    }
  }
```

## Событие изменения настроек треда

#### Query example:
```js
  {
    eventType: 'thread-on-settings-update',
    teamId: 'team id',
    data: {
      att: [],
      from: "",
      metadata: {
        userId: "initiator user id",
        // and fields which been updated
      },
      streamId: "stream id",
      threadId: "thread id",
      to: []
    }
  }
```
