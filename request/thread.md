### Support GET and POST HTTP methods

# Get thread:
```api.workonflow.com/{teamid}/thread/read/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | uniq id of thread      |
| statusId      | string        | Status ID (returns all threads with the indicated status) (optionally)  |
| statusIds     | array         | array uniq ids of status (optionally) |
| streamId      | string        | Stream ID (returns all threads in a stream) (optionally)    |
| ltUpdatedAt   | number | (Less than) Time limit for creation > less than  (optionally)  |
| gtUpdatedAt   | number        | (Greater than) Time limit for creation < greater than (optionally) |

### Query example:
```
  threadId: '5b0525134c0319001573485e',
  statusId: '5b0321234c0319001573485e',
  statusIds: ['5afd6d369a88ff00190baf79', '5afd6d369a88ff22190baf79', '5afd6d369a88ff00190bas12'],
  streamId: '5afd74659a88ff00190baf81',
  ltUpdatedAt: 1256953732,
  gtUpdatedAt: 1256953732
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread. See below example |

```
  data: [ {
    _id: 'thread id',
    archived: false,
    createdAt: 1524055334667,
    customFields: [],
    deadline: [],
    responsibleUserId: '',
    status: 'status id',
    streamId: 'stream id',
    teamId: 'team id',
    title: 'title name',
    customerId: 'id customer',
    customerIds: [],
    commentsFilter: {},
    type: '',
    roles: [responsible list],
    updatedAt: 1524056052883,
    position: -1900
  }, {
    если в запросе был указан statusId или streamId то тредов будет несколько
  }, {
    ...
  }]
```


# Create thread:
```api.workonflow.com/{teamid}/thread/create/{query}```

### Query:
|               |               |                                |
| ------------- |---------------| ----------------------:        |
| statusId      | string        | Status ID                      |
| streamId      | string        | Stream ID                      |
| title         | string        | name for thread                |
| deadline      | array         | deadline for task (optionally) |
| responsibleUserId | string    | id of user responsible (optionally) |
| customerId    | string        | id of external user (optionally) |
| roles         | string        | id followers of the thread (optionally) |

### Query example:
```
  statusId: '5b0321234c0319001573485e',
  streamId: '5afd74659a88ff00190baf81',
  title: 'New thread',
  deadline: [null, 1524902400000],
  responsibleUserId: '5afd74659a88ff0010988f81',
  customerId: '5afd74659a88ff0010988f81',
  roles: '5afd74659a88ff0010988f81'
```

### RESPONSES:
| code        | message | description           |
|:----------- |:--------|:----------------------|
| 200         | OK      | return new thread id. Example: data: '5afd74659a88ff0010900f81' |


# Get thread description:
```api.workonflow.com/1/thread.description/get/{query}```

### Query:
|               |               |                        |
| ------------- |---------------| ----------------------:|
| threadId      | string        | uniq id of thread      |

### Query example:
```
  threadId: '5b0321234c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:----------- |:--------|:----------------------|
| 200         | OK      | return description thread. See example below |

```
  data: [{
    content: "{}", // JSON format example below
    created: 1515487277798,
    editing: false,
    format: "draft.js",
    selection: null,
    teamId: "team id",
    updated: 1515487277798,
    _id: "description id"
  }]
```

example JSON description by content field:
```
"{"type":"doc","content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"strike"}],"text":"text"}]},{"type":"paragraph"},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"underline"}],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"em"}],"text":"text"}]},{"type":"paragraph","content":[{"type":"text","marks":[{"type":"strong"}],"text":"text"}]},{"type":"ordered_check_list","content":[{"type":"check_list_item","attrs":{"isCheck":false},"content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]}]}]},{"type":"ordered_list","content":[{"type":"list_item","attrs":{"id":null},"content":[{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text"}]}]}]},{"type":"ordered_number_list","attrs":{"order":1},"content":[{"type":"list_item","attrs":{"id":null},"content":[{"type":"paragraph"},{"type":"horizontal_rule"},{"type":"paragraph"}]}]},{"type":"paragraph","content":[{"type":"text","marks":[],"text":"text text"}]}]}"
```


# Thread set description
```api.workonflow.com/1/thread.description/set/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| content        | string        | some text for description |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  content: 'New description'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return id description. Example: data: "123nkh2o12831yqwe0912" |


# Thread set budget
```api.workonflow.com/{teamid}/thread.fields.budget/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| budget        | number        | Quantity of the thread’s budget |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  budget: 100
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread. See example below |

```
  data: {
    archived: false,
    budget: 100,
    createdAt: 1516366410022,
    customFields: [],
    customerId: "",
    deadline: [],
    position: -1600,
    responsibleUserId: "user id",
    roles: ["folowers ids"],
    status: "status id",
    streamId: "stream id",
    teamId: "team id",
    title: "thread name",
    type: "",
    updatedAt: 1524057103953,
    _id: "5b0321234c0319001573485e",
  }
```


# Thread set deadline
```api.workonflow.com/{teamid}/thread.fields.deadline/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| timestamp        | array        | An array of data in the format of a time stamp. The first element is the start of the thread and the second is its end (if the first element is given a value of null, the thread will only display a deadline). |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  timestamp: [null, 1524902400000]
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread. See example below |

```
  data: {
    archived: false,
    budget: 'number budget',
    createdAt: 'timestamp', // 1516366410022
    customFields: [],
    customerId: "",
    deadline: ['null or timestamp', 'timestamp'], // [null, 1524902400000]
    position: -1600,
    responsibleUserId: "user id",
    roles: ["folowers ids"],
    status: "status id",
    streamId: "stream id",
    teamId: "team id",
    title: "thread name",
    type: "",
    updatedAt: 'timestamp', // 1524057103953
    _id: "thread id",
  }
```


# Thread set priority
```api.workonflow.com/{teamid}/thread.fields.priority/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| priority        | string        | Priority level (one of two options: ‘HIGH’ or ‘NORMAL.’ Must be in upper case letters.) |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  priority: 'HIGH'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread. See example below |

```
  data: {
    archived: false,
    budget: 'number budget',
    createdAt: 'timestamp', // 1516366410022
    customFields: [],
    customerId: "",
    deadline: ['null or timestamp', 'timestamp'], // [null, 1524902400000]
    position: -1600,
    priority: "NORMAL",
    responsibleUserId: "user id",
    roles: ["folowers ids"],
    status: "status id",
    streamId: "stream id",
    teamId: "team id",
    title: "thread name",
    type: "",
    updatedAt: 'timestamp', // 1524057103953
    _id: "thread id",
  }
```


# Thread set responsible
```api.workonflow.com/{teamid}/thread.responsible/set/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  userId: '5b032123210319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with new responsible. See example below |

```
  data: {
    _id: 'thread id',
    archived: false,
    createdAt: 1524055334667,
    customFields: [],
    deadline: [],
    responsibleUserId: 'user id',
    status: 'status id',
    streamId: 'stream id',
    teamId: 'team id',
    title: '',
    customerId: '',
    customerIds: [],
    commentsFilter: {},
    type: '',
    roles: [ users ids list ],
    updatedAt: 1524057338518,
    position: -1900 }
  }
```


# Thread remove responsible
```PUT api.workonflow.com/{teamid}/thread.responsible/remove/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  userId: '5b032123210319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with without responsible. See example below |


# Thread set status
```api.workonflow.com/{teamid}/thread.status/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| statusId        | string        | id of status |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  statusId: '5b032123210319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with new status. See example below |


# Thread set points
```api.workonflow.com/{teamid}/thread.points/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| points        | number        | number of points |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  points: 20
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with new points. See example below |


# Thread set time to completion
```api.workonflow.com/{teamid}/thread.timetoc/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| timetocompletion        | number        | timestamp |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  timetocompletion: 1524057338518
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with new time to competion. See example below |


# Thread set stream
```api.workonflow.com/{teamid}/thread.stream/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| streamId        | string        | id of stream |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  streamId: '5b0321324c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with new stream. See example below |


# Thread set title
```api.workonflow.com/{teamid}/thread.title/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| title        | string        | new title for thread |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  title: 'New title for thread'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return object of thread with new title. See example below |


# Thread add customers
```api.workonflow.com/{teamid}/thread.externalfollowers/add/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| customerId        | string        | id of external user |
| customerIds   | array         | array of ids external users |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  customerId: '5b0321324c0319001573485e',
  customerIds: ['5b0321324c0319001573484q', '5e1451234c0319001573485e']
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Thread remove customers
```api.workonflow.com/{teamid}/thread.externalfollowers/remove/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| customerId        | string        | id of external user |
| customerIds   | array         | array of ids external users |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  customerId: '5b0321324c0319001573485e',
  customerIds: ['5b0321324c0319001573484q', '5e1451234c0319001573485e']
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Thread set followers
```api.workonflow.com/{teamid}/thread.followers/set/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  userId: '5b0321324c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Thread remove followers
```api.workonflow.com/{teamid}/thread.responsible/followers/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| threadId      | string        | id of thread         |
| userId        | string        | id of user |

### Query example:
```
  threadId: '5b0321234c0319001573485e',
  userId: '5b0321324c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |