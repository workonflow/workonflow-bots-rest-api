# Support Thread events

## Событие создания треда

#### Query example:
```js
  eventType: 'thread-on-created',
  teamId: 'team id',
  threadId: 'thread id',
  streamId: 'stream id',
  type: 'create',
  title: '',
  responsibleUserId: '',
  userId: 'id user creator'
```

## Событие обновления статуса треда

#### Query example:
```js
  eventType: 'thread-on-status-update',
  teamId: 'team id',
  threadId: 'thread id',
  streamId: 'stream id',
  statusId: 'status id',
  from: '',
  userId: 'id user initiator',
  prevStatusId: 'status id'
```

## Событие изменения настроек треда

#### Query example:
```js
  eventType: 'thread-on-settings-update',
  teamId: 'team id',
  from: "",
  userId: "initiator user id",
  streamId: "stream id",
  threadId: "thread id",
  fieldName: "",
  fieldPayload: ""
```
