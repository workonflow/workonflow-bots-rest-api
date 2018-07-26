# File actions

## file/geturl

**Метод для получения url файла который находится на Amazon**

```js
  api.workonflow.com/{teamid}/file/geturl/{query}
```

**Parameters:**

| field    | type   | description                            |
| ---------|--------| :------------------                    |
| fileId   | string | id of file                             |
| fileIds  | array  | Array of file IDs                      |
| filename | string | name of file                           | 
| url      | string | url для скачивания или просмотра файла |


**Query params example:**

```json
{
  "query":{
    "fileId":"5b0525134c0319001573485e",
    "fileIds": ["5afd6d369a88ff00190baf79", "5afd6d369a88ff22190baf79", "5afd6d369a88ff00190bas12"]
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": { "fileId":"5b0525134c0319001573485e" }}' https://api.workonflow.com/333ccc134c0319001573485e/comment/count
```

**Response example:**
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
---

## file/puturl

**Метод получения url для загрузки файла на Amazon**

```api.workonflow.com/{teamid}/file/puturl/{query}```

**Parameters:**

| field         | type   | description            |
| ------------- |--------| ----------------------:|
| filename      | string | fileName.format        |
| size          | number | file size in bytes     |

**Query params example:**

```json
{
  "query":{
    "filename":"foto",
    "size":2256
  }
}
```

**Query example:**

```js
  curl -H "Content-Type: application/json" -X POST -d '{"query": {"filename":"foto", "size":"2256"}}' https://api.workonflow.com/333ccc134c0319001573485e/comment/count
```

**Response example:**

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
