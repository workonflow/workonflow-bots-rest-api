# In developing

# Call requests

### call/get

**Метод получения звонка**

```js
  https://botapi.workonflow.com/{teamid}/call/get
```

**Parameters**

| field         | type          | description         | required |
| ------------- |---------------| -----------------   |----------|
| threadId      | string        | id of thread        | yes      |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call/get
```

**Response example:**

```js
{
  code: 200,
  message: 'OK',
  data:
  {
    destinationId: '5bcda4d25ad71w0015771257',
    streamId: '5bbc67c5522e2400149af76c',
    originateUserId: '{"contactId":"5bcda4d2e74419001f6fe4b1","phone":"07112749","trunkId":"bambYXY3o"}',
    typeDestination: 'thread-incoming',
    destinationContacts: '[{"contactId":"5b72aaab444507001c8be443","isMute":false,"isHold":false,"isMeInvite":false,"isExtension":false,"answered":false,"isBot":false,"hasOriginator":false},{"contactId":"2bcda4d2e74419001f6fe4f0","answered":true,"hasOriginator":true,"channelId":"558d25da-d6e4-11e8-bd3d-4799aea902e9","isMute":false,"createdAt":"1540203730669","isHold":false,"phone":"07112749","trunkId":"bambYVY3o","isMeInvite":false,"isExtension":false,"isBot":false}]'
  }
}
```

---


### call/invite

**Метод для приглашения пользователя(лей) в звонок**

```js
  https://botapi.workonflow.com/{teamid}/call.user/invite
```

**Parameters**

| field         | type          | description         | required |
| ------------- |---------------| -----------------   |----------|
| threadId      | string        | id of thread        | yes      |
| contactId     | string     | id of user             | yes       |
| phone         | string        | number phone          |
| userIds: [ { contactId, phone } ]       | array         | array of users ids with phone number  | yes      |

> **Важно!** Обязательно предоставить либо contactId либо userIds

**Body message example:**

```json
  {
    threadId: "5bcdb5535ad82d00157712c5",
    contactId: "5b72aaab444507001b8sw553",
    phone: "89999999999"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.user/invite
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call/kick

**Метод для исключения пользовател(лей)/тредов и прочего**

```js
  https://botapi.workonflow.com/{teamid}/call/kick
```

**Parameters**

| field         | type          | description         | required |
| ------------- |---------------| -----------------   |----|
| threadId      | string        | id of thread        | yes |
| contactId        | string        | id of user          |
| phone       | string         | phonenumber  |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "userId": "5b4458eb1b2b33001bf213bf" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call/kick
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.user/hold

**Метод для постановки пользователя на паузу**

```js
  https://botapi.workonflow.com/{teamid}/call.user/hold
```

**Parameters**

| field         | type          | description         | required |
| ------------- |---------------| -----------------   |---|
| threadId      | string        | id of thread        | yes |
| contactId        | string        | id of user          |
| phone       | number         | phonenumber  |



**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "contactId":"5b0525134c031900157348xd"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "contactId":"5b0525134c031900157348xd" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.user/hold
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---


### call.user/unhold

**Метод для снятия пользователя с паузы**

```js
  https://botapi.workonflow.com/{teamid}/call/unpause
```

**Parameters**

| field         | type          | description         | required |
| ------------- |---------------| -----------------   |---|
| threadId      | string        | id of thread        | yes |
| contactId        | string        | id of user          |
| phone       | number         | phonenumber  |

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "contactId":"5b0525134c031900157348xd"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "contactId":"5b0525134c031900157348xd" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.user/unhold
```


**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.audio/play

**Метод для загрузки и проигрывания аудиозаписи в звонке (для всех пользователей или для конкретных?)**

```js
  https://botapi.workonflow.com/{teamid}/call.audio/play
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| isLoop        | boolean       | loop audio file or not|
| url       | string        | url of file, intended to play|

> **Важно!** Аудиофайл должен иметь расширение mp3 или wav и не должен превышать размера в 10мб.

**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "url": "https://url.to.your/audiofile.mp3",
    "isLoop": true
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "isLoop": true, "url": "https://url.to.your/audiofile.mp3"}' https://botapi.workonflow.com/333ccc134c0319001573485e/call.audio/play
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.audio/stop

**Метод для остановки проигрывания аудиозаписи в звонке (для всех пользователей или для конкретных?)**

```js
  https://botapi.workonflow.com/{teamid}/call.audio/stop
```

**Parameters**

| field         | type          | description         |
| ------------- |---------------| -----------------   |
| threadId      | string        | id of thread        |
| url       | string        | url of file, intended to stop|


**Body message example:**

```json
  {
    "threadId":"5b0525134c0319001573485e",
    "url": "https://url.to.your/audiofile.mp3"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e", "url": "https://url.to.your/audiofile.mp3"}' https://botapi.workonflow.com/333ccc134c0319001573485e/call.audio/stop
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.recording/start

**Метод для начала записи разговора в звонке**

```js
  https://botapi.workonflow.com/{teamid}/call.recording/start
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
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.recording/start
```

**Response example:**

```js
  { code: 200, message: "OK" }
```

---

### call.recording/stop

**Метод для остановки записи разговора в звонке**

```js
  https://botapi.workonflow.com/{teamid}/call.recording/stop
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
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.recording/stop
```

**Response example:**

```js
  { code: 200, message: "OK", data: { fileUrl: 'https://url.to.your.recorded.dialog/audiofile.mp3' } }
```

---

### call.stream/start

**Метод для начала стрима разговора в звонке**

```js
  https://botapi.workonflow.com/{teamid}/call.stream/start
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
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.stream/start
```

**Response example:**

```js
  { code: 200, message: "OK", data: { streamUrl: 'https://url.to.your.recorded.dialog/audiofile.mp3' } }
```

---

### call.stream/stop

**Метод для остановки стрима разговора в звонке**

```js
  https://botapi.workonflow.com/{teamid}/call.stream/stop
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
  curl -H "Content-Type: application/json" -X POST -d '{ "threadId":"5b0525134c0319001573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/call.stream/stop
```

**Response example:**

```js
  { code: 200, message: "OK" }
```
