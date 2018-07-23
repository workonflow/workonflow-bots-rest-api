# Support Comment events

## Событие создания коментария

#### Query example:
```js
  { 
    eventType: 'comment-on-created',
    teamId: 'some team id',
    data: {
      id: 'comment id',
      userId: 'some user id',
      content: {
        createdAt: 1524043332761,
        updatedAt: 1524043332761,
        to: [ 'bot id' ],
        from: 'user id',
        att:  [ { type: 'text', data: { text: 'some text' } } ],
        _id: 'comment id',
      }
    }
  }
```

## Событие создания комментария в личном чате пользователя с ботом

#### Query example:
```js
  { 
    eventType: 'comment-on-direct',
    teamId: 'some team id',
    data: {
      id: 'comment id',
      userId: 'some user id',
      content: {
        createdAt: 1524043332761,
        updatedAt: 1524043332761,
        to: [ 'bot id' ],
        from: 'user id',
        att:  [ { type: 'text', data: { text: 'some text' } } ],
        _id: 'comment id',
      }
    }
  }
```

## События создания коментария с упоминанием бот-id

### In stream

#### Query example:
```js
  { 
    eventType: 'comment-on-mention-in-stream',
    teamId: 'some team id',
    data: {
      id: 'comment id',
      userId: 'some user id',
      content: {
        createdAt: 1524043332761,
        updatedAt: 1524043332761,
        to: [ 'bot id' ],
        from: 'user id',
        att:  [ { type: 'text', data: { text: '@botId@ some text' } } ],
        streamId: 'some stream id',
        _id: 'comment id',
      }
    }
  }
```

### In thread

#### Query example:
```js
  { 
    eventType: 'comment-on-mention-in-thread',
    teamId: 'some team id',
    data: {
      id: 'comment id',
      threadId: 'some thread id',
      userId: 'some user id',
      content: {
        createdAt: 1524043332761,
        updatedAt: 1524043332761,
        to: [ 'bot id' ],
        from: 'user id',
        att:  [ { type: 'text', data: { text: '@botId@ some text' } } ],
        threadId: 'some thread id',
        streamId: 'some stream id',
        _id: 'comment id',
      }
    }
  }
```
