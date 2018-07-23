### Support GET and POST HTTP methods

# Mail

# Method for obtaining email channels
```api.workonflow.com/{teamid}/channel.mail/get/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| userId        | string        | User ID (returns array of available channels) |
| userIds       | array         | Array of user IDs (analogous to id) (optionally)  |
| email         | string        | Mail channel (returns channel with indicated email address, optionally) |

### Query example:
```
  userId: '5b0525134c0319001573485e',
  userIds: ['5b0525134c03190015734abe', '5b0525134c03190015734851'],
  email: 'email@email.com'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return object account email. See example below|

```
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
  }, {
    ...
  }]
```


# Method for receiving email channels
```api.workonflow.com/{teamid}/channel.mail/read/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| emailId        | string        | email ID |
| emailIds       | array         | Array of email IDs (optionally)  |

### Query example:
```
  emailId: '5b0525134c0319001573485e',
  emailIds: ['5b0525134c03190015734abe', '5b0525134c03190015734851'],
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return object email channel. See example below|

```
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
```


# Method for sending email
```api.workonflow.com/{teamid}/channel.mail/send/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| from        | string        | Must indicate an email channel |
| to          | string        | Email of recipient  |
| html       | string         | HTML layout for the letter. It not indicated in the letter, the text parameter will be displayed.  |
| messageId     | string        | ID of message in the form of an email client (leave blank if unknown) |
| subject       | string        | Subject of message |
| text          | string        | Text of message (displayed in the absence of an HTML layout)  |
| threadId      | string        | Thread ID |

### Query example:
```
  from: 'fromEmail@email.com',
  to: 'toEmail@email.com',
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return object email channel. See example below|


# Telephony

# Create user SIP
```api.workonflow.com/{teamid}/channel.telephony/creat/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| username        | string        | user name |
| password          | string        | user pass  |
| domain          | string        | domain  |
| contactId          | string        | User ID  |


# Method for deleting user SIP from telephony (still in development)
```api.workonflow.com/{teamid}/channel.telephony/delete/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| sipId        | string        | SIP ID |


# Method for obtaining user SIP
```api.workonflow.com/{teamid}/channel.telephony/get/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| username        | string        | user name |
| sipId          | string        | SIP ID  |
| contactId          | string        | User ID  |


# Update user SIP method
```api.workonflow.com/{teamid}/channel.telephony/update/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| username        | string        | user name |
| password          | string        | user pass  |
| domain          | string        | domain  |
| contactId          | string        | User ID  |
