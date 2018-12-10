# File requests

## Метод для получения url файла который находится на Amazon

```https://botapi.workonflow.com/{teamid}/file/get.url```

### Параметры:
> **Внимание!** Одно из полей обязательно должно быть передано в запросе: fileId, fileIds

| field    | type   | description                            |
| ---------|--------| :------------------                    |
| fileId   | string | идентификатор файла|
| fileIds  | array  | массив индетификаторов файлов |


### Пример тела запроса:

```json
{
  "fileId":"5b0525134c0319001573485e"
}
```

### Пример запроса с помощью curl:

```curl -H "Content-Type: application/json" -X POST -d '{ "fileId" : "5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/file/get.url```

### Пример ответа:
```json
{
  "code": 200,
  "message": "OK",
  "data": {
    "filename": "foto",
    "fileId": "5ad9970e24c5c900177624cf",
    "url": "https://s3.eu-central-1.amazonaws.com/storage.teslatele.com/5af979addb6cec001515779b/image.png?X-Amz-Algorithm=AWSAC-SHA256&X-Amz-Credential=AKIAJ7FMTV4FQA%2F20180725%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20180725T091&X-Amz-Expires=259200&X-Amz-Signature=5c6a9d6d1b418792fa64ce78545f88f2ca9695844fd8b6127d6c683697861528&X-Amz-SignedHeaders=host"
  }
}
```

## Метод получения url для загрузки файла на Amazon

```https://botapi.workonflow.com/{teamid}/file/put.url```

### Параметры:
> **Внимание!** Одно из полей обязательно должно быть передано в запросе: filename, filenames

| field         | type   | description            |
| ------------- |--------| ----------------------:|
| filename      | string | имя файла с расширением        |
| filenames     | array  | массив имен файлов |
| size          | number | размер файла в байтах     |
| streamId      | string | идентификатор стрима|
| threadId      | string | идентификатор треда |
| authorId      | string | идентификатор автора файла |

### Пример тела запроса:

```json
{
  "filename":"foto.jpg",
  "size":2256
}
```

### Пример запроса с помощью curl:

```curl -H "Content-Type: application/json" -X POST -d '{ "filename":"foto.jpg", "size":"2256" }' https://botapi.workonflow.com/333ccc134c0319001573485e/file/put.url```

### Пример ответа:
```json
{
 "code": 200,
  "message": "OK",
  "data": {
    "id": "5b0525134c0319001573485e",
    "url": "https://s3.eu-central-1.amazonaws.com/storage.teslatele.com/5af979addb6cec001515779b/image.png?X-Amz-Algorithm=AWSAC-SHA256&X-Amz-Credential=AKIAJ7FMTV4FQA%2F20180725%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20180725T091&X-Amz-Expires=259200&X-Amz-Signature=5c6a9d6d1b418792fa64ce78545f88f2ca9695844fd8b6127d6c683697861528&X-Amz-SignedHeaders=host"
  }
}
```

## Метод получения файлов в workonflow

```https://botapi.workonflow.com/{teamid}/file/read```

### Параметры:
> **Внимание!** Одно из полей обязательно должно быть передано в запросе:  id, streamId, ids, threadId, authorId

| field         | type   | description            |
| ------------- |--------| ----------------------:|
| id      | string | идентификатор файла        |
| ids     | array  | массив идентификаторов файлов |
| skip          | number |  кол-во файлов которые необходимо пропустить  |
| streamId      | string | идентификатор стрима |
| threadId      | string | идентификатор треда |
| authorId      | string | идентификатор автора файла |
| limit         | number | число файлов, которые нужно показать за один запрос |

### Пример тела запроса:
```json
{
  "authorId": "333ccc134c0319001573485b",
  "limit": 1
}
```

### Пример запроса с помощью curl:
```curl -H "Content-Type: application/json" -X POST -d '{ "authorId":"333ccc134c0319001573485b", "limit": 1 }' https://botapi.workonflow.com/333ccc134c0319001573485e/file/read```

### Пример ответа:
```json
{
 "code": 200,
  "message": "OK",
  "data": [
    {
      "authorId": "333ccc134c0319001573485b",
      "createdAt": 1537963580987,
      "filename": "shapshot.png",
      "id": "5bab763cc444420015ea8eef",
      "size": 19170,
      "streamId": "123b405b81d3f8001497603d",
      "threadId": null
    }
  ]
}
```
