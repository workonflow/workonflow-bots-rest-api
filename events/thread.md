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

## Событие изменения треда

#### Query example:
```js
  eventType: 'thread-on-update',
  teamId: 'team id',
  from: "",
  userId: "initiator user id",
  streamId: "stream id",
  threadId: "thread id",
  fieldName: "",
  fieldPayload: ""
```
