# Mail requests

## Method for obtaining email channels
```https://botapi.workonflow.com/{teamid}/channel.mail/account.get/{body}```

### Parameters:
| name      |type            | description                       |
| ------------- |---------------| ----------------------|
| userId        | string        | User ID (returns array of available channels) |
| userIds       | array         | Array of user IDs (analogous to id) (optionally)  |
| email         | string        | Mail channel (returns channel with indicated email address, optionally) |

### Body message example:
```json
  {
    userId: "5b0525134c0319001573485e",
    userIds: [ "5b0525134c03190015734abe", "5b0525134c03190015734851"],
    email: "email@email.com"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "userId":"5b0525134c0319121573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.mail/account.get
```
### Response:
```json
  {
    code: 200,
    message: OK,
    data: [{
      email: "channel mail",
      name: "name channel",
      outgoing: false,
      private: false,
      status: true,
      streamId: "stream id",
      teamId: "team id",
      token: "",
      userId: "creator user id",
      _id: "channel id"
    }]
  }
```

# Method for receiving email channels
```https://botapi.workonflow.com/{teamid}/channel.mail/read/{body}```

### Parameters:
> **Warning!** One of the fields required

|  name          |    type  |  description  |
| ------------- |---------------| ----------------------:|
| id        | string        | email ID |
| ids       | array         | Array of email IDs (optionally)  |

### Body message example:
```js
  {
    id: '5b0525134c0319001573485e',
    // or
    ids: ['5b0525134c03190015734abe', '5b0525134c03190015734851'],
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "id":"5b0525134c0319121573485e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.mail/read
```
### Response:
```
  {
    code: 200,
    message: OK,
    data: [{
      accountId: "channel id",
      attachments: [],
      cc: null,
      conversationId: "conversation id",
      date: "create date", // example format Fri, 20 Apr 2018 11:53:18 +0300
      from: "ereskoe@list.ru",
      headers: "header",
      html: "html mail",
      inReplyTo: null,
      messageId: "message id in mail client format", // example <1524214398.529320890@f338.i.mail.ru>
      name: "contact name",
      receivedDate: "date response mail", // example format Fri, 20 Apr 2018 11:53:18 +0300
      references: null,
      streamId: "",
      subject: "subject title mail",
      teamId: "team id",
      text: "text mail",
      threadId: "thread id",
      to: "channel mail",
      type: "incoming",
      _id: "conversation id",
    }, {
      // если запрос был по ids, вернёт несколько елементов
    }, {
      ...
    }]
  }
```


# Method for sending email
```https://botapi.workonflow.com/{teamid}/channel.mail/send/{body}```

### Parameters:
|  name     |   type | description  | required |
| ------------- |---------------| ----------------------:|---:|
| from        | string        | Must indicate an email channel | yes |
| to          | string        | Email of recipient  | yes |
| html       | string         | HTML layout for the letter. It not indicated in the letter, the text parameter will be displayed.  |
| messageId     | string        | ID of message in the form of an email client (leave blank if unknown) |
| subject       | string        | Subject of message |
| text          | string        | Text of message (displayed in the absence of an HTML layout)  |
| threadId      | string        | Thread ID | yes|

### Body message example:
```json
  {
    from: 'fromEmail@email.com',
    to: 'toEmail@email.com',
    subject: 'new mail',
    text: 'Hello, world!'
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "from": "fromEmail@email.com", "to": "toEmail@email.com", "subject": "new mail", "text": "Hello, world!" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.mail/send
```
### Response:
```json
  {
    code: 200,
    message: OK
  }
```

# Telephony

# Create user SIP
```https://botapi.workonflow.com/{teamid}/channel.telephony/create/{body}```

### Parameters:
|  name   |  type  | description | required |
| ------------- |---------------| ----------------------:|---:|
| username        | string        | user name | yes |
| password          | string        | user password  | yes |
| domain          | string        | domain  | yes |
| contactId          | string        | User ID  | yes |

### Body message example
```json
  {
    "username": "John Wick",
    "password": "somePassForJohn",
    "domain": "john@pbx.com",
    "contactId":  "333ccc134c0319001543481e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "username": "John Wick", "password": "somePassForJohn", "domain": "john@pbx.com", "contactId": "333ccc134c0319001543481e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/create
```
### Response:
```json
  {
    code: 200,
    message: OK,
    data: { id: "33s231134c0319001543481e"}
  }
```


# Method for deleting user SIP from telephony (still in development)
```https://botapi.workonflow.com/{teamid}/channel.telephony/delete/{body}```

### Parameters:
|  name   |  type  |   description  | required |
| ------------- |---------------| ----------------------:|---:|
| sipId        | string        | SIP ID | yes|
### Body message example
```json
  {
    "sipId":  "333cbv134c0319001543481e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "sipId": "333cbv134c0319001543481e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/delete
```
### Response:
```json
  {
    code: 200,
    message: OK
  }
```


# Method for obtaining user SIP
```https://botapi.workonflow.com/{teamid}/channel.telephony/get/{body}```

### Parameters:
|  name       |  type  | description   |
| ------------- |---------------| ----------------------:|
| username        | string        | user name |
| sipId          | string        | SIP ID  |
| contactId          | string        | User ID  |
### Body message example
```json
  {
    "username": "John Wick",
    "sipId": "392ccc134c0319001543481b",
    "contactId":  "333ccc134c0319001543481b"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "username": "John Wick", "sipId": "392ccc134c0319001543481b", "contactId": "333ccc134c0319001543481b" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/get
```
### Response:
```json
  {
    code: 200,
    message: OK
  }
```


# Update user SIP method
```https://botapi.workonflow.com/{teamid}/channel.telephony/update/{body}```

### Parameters:
|  name      |  type  | description   | required |
| ------------- |---------------| ----------------------:|-----:|
| username        | string        | user name | yes |
| password          | string        | user pass  | yes |
| domain          | string        | domain  | yes|
| contactId          | string        | User ID  | yes |
### Body message example
```json
  {
    "username": "John Wick",
    "password": "somePassForJohn",
    "domain": "john@pbx.com",
    "contactId": "333ccc134c0319001543481e"
  }
```
**Request example:**
```js
  curl -H "Content-Type: application/json" -X POST -d '{ "username": "John Wick", "password": "somePassForJohn", "domain": "john@pbx.com", "contactId": "333ccc134c0319001543481e" }' https://botapi.workonflow.com/333ccc134c0319001573485e/channel.telephony/update
```
### Response:
```json
  {
    code: 200,
    message: OK
  }
```
