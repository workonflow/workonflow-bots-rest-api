# Метод для создания статуса потока
```POST api.workonflow.com/1/status/create/{query}```

```
query: {
  name: 'new status name',
  streamId: 'streamId',
  type: 'Done',
  color: '#c0c0c0'
}
```

# Метод для получения статуса
```GET api.workonflow.com/1/status/read/{query}```

```
query: {
  id: 'statusId',
  streamId: 'streamId'
}
```

# Метод для изменения имени статуса
```PUT api.workonflow.com/1/status/set-name/{query}```

```
query: {
  id: 'statusId',
  name: 'new name of status'
}
```
