# In developing

# Call requests

### call/start

**Метод создания звонка в задаче**

```js
  api.workonflow.com/{teamid}/call/start/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| direction     | string        | direction of call   |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call/start
```

**Response example:**

```js
  { code: 200, message: "OK", data: { direction } }
```

---

### call/end

**Метод завершения звонка в задаче**

```js
  api.workonflow.com/{teamid}/call/end/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| direction     | string        | direction of call   |
| callDuration  | integer       | full call time in seconds|
| dialogDuration| integer       | talk time in seconds|
| result        | string        | result of the call  |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call/end
```

**Response example:**

```js
  { code: 200, message: "OK", data: { callDuration, dialogDuration, result, direction } }
```

---

### call.user/invite

**Метод для приглашения пользователя(лей) в звонок**

```js
  api.workonflow.com/{teamid}/call.user/invite/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| userId        | string        | id of user          |
| userIds       | array         | array of users ids  |
| invitedUsersCount| string     | number of invited users|

> **Важно!** Обязательно предоставить либо userId либо userIds. При наличии обоих полей userIds будет проигнорирован.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "userId": "5b4458eb1b2b33001bf213bf" // or "userIds": [ "5b4458eb1b2b33001bf213bf", "5b4458eb1b2b33001bf213bc"]
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://api.workonflow.com/333ccc134c0319001573485e/call.user/invite
```

**Response example:**

```js
  { code: 200, message: "OK", data: { invitedUsersCount: 1 } }
```

---

### call.user/exclude

**Метод для исключения пользовател(лей) из звонка**

```js
  api.workonflow.com/{teamid}/call.user/exclude/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| userId        | string        | id of user          |
| userIds       | array         | array of users ids  |
| excludedUsersCount| string    | number of excluded users|

> **Важно!** Обязательно предоставить либо userId либо userIds. При наличии обоих полей userIds будет проигнорирован.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "userId": "5b4458eb1b2b33001bf213bf" // or "userIds": [ "5b4458eb1b2b33001bf213bf", "5b4458eb1b2b33001bf213bc"]
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://api.workonflow.com/333ccc134c0319001573485e/call.user/exclude
```

**Response example:**

```js
  { code: 200, message: "OK", data: { excludedUsersCount: 1 } }
```

---

### call/pause

**Метод для постановки звонка на паузу**

```js
  api.workonflow.com/{teamid}/call/pause/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| userId        | string        | id of user          |
| userIds       | array         | array of users ids  |
| pausedUsersCount| string      | number of users switched on pause|

> **Важно!** Обязательно предоставить либо userId либо userIds. При наличии обоих полей userIds будет проигнорирован.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "userId": "5b4458eb1b2b33001bf213bf" // or "userIds": [ "5b4458eb1b2b33001bf213bf", "5b4458eb1b2b33001bf213bc"]
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://api.workonflow.com/333ccc134c0319001573485e/call/pause
```

**Response example:**

```js
  { code: 200, message: "OK", data: { pausedUsersCount: 1 } }
```

---

### call/unpause

**Метод для снятия звонка с паузы**

```js
  api.workonflow.com/{teamid}/call/unpause/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| userId        | string        | id of user          |
| userIds       | array         | array of users ids  |
| unpausedUsersCount| string    | number of users switched off pause|

> **Важно!** Обязательно предоставить либо userId либо userIds. При наличии обоих полей userIds будет проигнорирован.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "userId": "5b4458eb1b2b33001bf213bf" // or "userIds": [ "5b4458eb1b2b33001bf213bf", "5b4458eb1b2b33001bf213bc"]
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://api.workonflow.com/333ccc134c0319001573485e/call/unpause
```

**Response example:**

```js
  { code: 200, message: "OK", data: { unpausedUsersCount: 1 } }
```

---

### call/unpause

**Метод для снятия звонка с паузы**

```js
  api.workonflow.com/{teamid}/call/unpause/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| userId        | string        | id of user          |
| userIds       | array         | array of users ids  |
| unpausedUsersCount| string    | number of users switched off pause|

> **Важно!** Обязательно предоставить либо userId либо userIds. При наличии обоих полей userIds будет проигнорирован.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "userId": "5b4458eb1b2b33001bf213bf" // or "userIds": [ "5b4458eb1b2b33001bf213bf", "5b4458eb1b2b33001bf213bc"]
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://api.workonflow.com/333ccc134c0319001573485e/call/unpause
```

**Response example:**

```js
  { code: 200, message: "OK", data: { unpausedUsersCount: 1 } }
```

---

### call.audio/play

**Метод для загрузки и проигрывания аудиозаписи в звонке (для всех пользователей или для конкретных?)**

```js
  api.workonflow.com/{teamid}/call.audio/play/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| fileUrl       | string        | url of file, intended to play|

> **Важно!** Аудиофайл должен иметь расширение mp3 или wav и не должен превышать размера в 10мб.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "fileUrl": "https://url.to.your/audiofile.mp3"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "fileUrl": "https://url.to.your/audiofile.mp3"}' https://api.workonflow.com/333ccc134c0319001573485e/call.audio/play
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.audio/stop

**Метод для остановки проигрывания аудиозаписи в звонке (для всех пользователей или для конкретных?)**

```js
  api.workonflow.com/{teamid}/call.audio/stop/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call.audio/stop
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.recording/start

**Метод для начала записи разговора в звонке**

```js
  api.workonflow.com/{teamid}/call.recording/start/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call.recording/start
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.recording/stop

**Метод для остановки записи разговора в звонке**

```js
  api.workonflow.com/{teamid}/call.recording/stop/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| fileUrl       | string        | url of file, with recorded dialog|

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call.recording/stop
```

**Response example:**

```js
  { code: 200, message: "OK", data: { fileUrl: 'https://url.to.your.recorded.dialog/audiofile.mp3' } }
```

---

### call.stream/start

**Метод для начала стрима разговора в звонке**

```js
  api.workonflow.com/{teamid}/call.stream/start/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| streamUrl     | string        | url, with streaming dialog|

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call.stream/start
```

**Response example:**

```js
  { code: 200, message: "OK", data: { streamUrl: 'https://url.to.your.recorded.dialog/audiofile.mp3' } }
```

---

### call.stream/stop

**Метод для остановки стрима разговора в звонке**

```js
  api.workonflow.com/{teamid}/call.stream/stop/{body}
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://api.workonflow.com/333ccc134c0319001573485e/call.stream/stop
```

**Response example:**

```js
  { code: 200, message: "OK" }
```
