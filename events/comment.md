# Support Comment events

## Событие создания коментария

#### Query example:
```js
  eventType: 'comment-on-created',
  teamId: 'some team id',
  id: 'comment id',
  userId: 'some user id',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  to: 'bot id',
  from: 'user id',
  attText: 'some text',
```

## Событие создания комментария в личном чате пользователя с ботом

#### Query example:
```js
  eventType: 'comment-on-direct',
  teamId: 'some team id',
  id: 'comment id',
  userId: 'some user id',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  to: 'bot id',
  from: 'user id',
  attText: 'some text',
```

## События создания коментария с упоминанием бот-id

### In stream

#### Query example:
```js
  eventType: 'comment-on-mention-in-stream',
  teamId: 'some team id',
  id: 'comment id',
  userId: 'some user id',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  to: 'bot id',
  from: 'user id',
  attText: '@botId@ some text',
  streamId: 'some stream id',
```

### In thread

#### Query example:
```js
  eventType: 'comment-on-mention-in-thread',
  teamId: 'some team id',
  id: 'comment id',
  threadId: 'some thread id',
  userId: 'some user id',
  createdAt: 1524043332761,
  updatedAt: 1524043332761,
  to: 'bot id',
  from: 'user id',
  att: '@botId@ some text',
  streamId: 'some stream id',
```
