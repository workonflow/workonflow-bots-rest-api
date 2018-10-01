# File requests

## file/get.url

**Метод для получения url файла который находится на Amazon**

```js
  https://botapi.workonflow.com/{teamid}/file/get.url/{body}
```

**Parameters:**
> **Warning!** One of the fields (fileId or fileIds) required

| field    | type   | description                            |
| ---------|--------| :------------------                    |
| fileId   | string | id of file                             |
| fileIds  | array  | Array of file IDs                      |


**Body message example:**

```json
{
  "fileId":"5b0525134c0319001573485e",
  // or
  "fileIds": ["5afd6d369a88ff00190baf79", "5afd6d369a88ff22190baf79", "5afd6d369a88ff00190bas12"]
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "fileId" : "5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/file/get.url
```

**Response :**
```js
{
  code: 200,
  message: 'OK',
  data: {
    filename: 'foto',
    fileId: '5ad9970e24c5c900177624cf',
    url: 'https://s3.eu-central-1.amazonaws.com/storage.teslatele.com/5af979addb6cec001515779b/image.png?X-Amz-Algorithm=AWSAC-SHA256&X-Amz-Credential=AKIAJ7FMTV4FQA%2F20180725%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20180725T091&X-Amz-Expires=259200&X-Amz-Signature=5c6a9d6d1b418792fa64ce78545f88f2ca9695844fd8b6127d6c683697861528&X-Amz-SignedHeaders=host'
  }
}
```

## file/put.url

**Метод получения url для загрузки файла на Amazon**

```https://botapi.workonflow.com/{teamid}/file/put.url/{body}```

**Parameters:**
> **Warning!** One of the fields (filename or filenames) required

| field         | type   | description            |
| ------------- |--------| ----------------------:|
| filename      | string | fileName.extension        |
| filenames     | array  | array with filenames |
| size          | number | file size in bytes     |
| streamId      | string | id of stream |
| threadId      | string | id of thread |
| authorId      | string | id of author |

**Body message example:**

```json
{
  "filename":"foto.jpg",
  "size":2256
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "filename":"foto.jpg", "size":"2256" }' https://botapi.workonflow.com/333ccc134c0319001573485e/file/put.url
```

**Response :**

```js
{
  code: 200,
  massage: 'OK',
  data: {
    id: "5b0525134c0319001573485e"
    url: "https://s3.eu-central-1.amazonaws.com/storage.teslatele.com/5af979addb6cec001515779b/image.png?X-Amz-Algorithm=AWSAC-SHA256&X-Amz-Credential=AKIAJ7FMTV4FQA%2F20180725%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Date=20180725T091&X-Amz-Expires=259200&X-Amz-Signature=5c6a9d6d1b418792fa64ce78545f88f2ca9695844fd8b6127d6c683697861528&X-Amz-SignedHeaders=host"
  }
}
```

## file/read

**Метод получения файлов в workonflow**

```https://botapi.workonflow.com/{teamid}/file/read/{body}```

**Parameters:**
> **Warning!** One of the fields (id, streamId, ids, threadId, authorId) required

| field         | type   | description            |
| ------------- |--------| ----------------------:|
| id      | string | id of file        |
| ids     | array  | array with ids of files |
| skip          | number |  кол-во файлов которые необходимо пропустить  |
| streamId      | string | id of stream |
| threadId      | string | id of thread |
| authorId      | string | id of author |
| limit         | number | число файлов, которые нужно показать за один запрос |

**Body message example:**

```json
{
  "authorId": "333ccc134c0319001573485b",
  "limit": 1
}
```

**Request example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{ "authorId":"333ccc134c0319001573485b", "limit": 1 }' https://botapi.workonflow.com/333ccc134c0319001573485e/file/read
```

**Response :**

```js
{
  code: 200,
  message: "OK",
  data: [
    {
      authorId: "333ccc134c0319001573485b"
      createdAt: 1537963580987
      filename: "shapshot.png"
      id: "5bab763cc444420015ea8eef"
      size: 19170
      streamId: "123b405b81d3f8001497603d"
      threadId: null
    }
  ]
}
```
