### support GET and POST HTTP methods

# Метод для получения url файла с Amazon
```api.workonflow.com/{teamid}/file/geturl/{query}```

### Query:
| field         | type          | description            |
| ------------- |---------------| ----------------------:|
| fileId          | string        | id of file   |
| fileIds       | array       | Array of file IDs  |

### Query example:
```
  fileId: '5b0525134c0319001573485e',
  fileIds: ['5afd6d369a88ff00190baf79', '5afd6d369a88ff22190baf79', '5afd6d369a88ff00190bas12']
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return info about file. See example below    |

```
  data: {
    filename: "fileName.format",
    id: "file id",
    url: "url address for upload file"
    urlPreview: null
  }
```


# Метод получения url для загрузки файла на Amazon
```api.workonflow.com/{teamid}/file/puturl/{query}```

### Query:
| field         | type          | description            |
| ------------- |---------------| ----------------------:|
| authorId          | string        | id of user   |
| filename       | string       | fileName.format  |
| size          | number        | file size |
| streamId      | string        | id of stream  |
| threadId      | string        | id of thread (optionally) |

### Query example:
```
  fileId: '5b0525134c0319001573485e',
  fileIds: ['5afd6d369a88ff00190baf79', '5afd6d369a88ff22190baf79', '5afd6d369a88ff00190bas12']
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return info about file. See example below    |

```
  data: {
    id: "file id"
    url: "url address for download file"
  }
```
