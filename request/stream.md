### Support GET and POST HTTP methods

# Create stream
```api.workonflow.com/{teamid}/stream/create/{query}```

### Query:

|               |               |                       |
| ------------- |---------------| ----------------------:|
| name          | string        | new name for stream   |
| isEmpty       | boolean       | по умолчанию поток создаётся с 3мя статусами, если указать данный параметр будет создан пустой поток  |
| settings      | string/array/object | settings for stream |

### Query example:
```
  name: 'New stream',
  isEmpty: true,
  settings: {
  roles: [],
  seenBy: {},
  settings: {
    widgets: {
      DataTime: {on: true, options: "deadline", type: "DataTime"},
      ExternalFollowers: {on: true, type: "ExternalFollowers"},
      Priority: {on: true, type: "Priority"},
      Responsible: {on: true, type: "Responsible"},
      StreamSelect: {on: true, type: "StreamSelect"},
      WorkflowStatus: {on: true, type: "WorkflowStatus"},
  },
  threadPrioritites: [],
  threadStatuses: [],
  visibility: []
}
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return new stream id  |


# Delete stream
```api.workonflow.com/{teamid}/stream/delete/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |

### Query example:
```
  streamId: '5b0525134c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream read
```api.workonflow.com/{teamid}/stream/read/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId      | string        | uniq id of stream (optionally)     |
| streamIds     | array of string | array uniq ids of stream  (optionally)|

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  streamIds: ['5b0525134c0319001573485e', '5b0525134c0319001573485e']
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return stream object. See example below  |

```
  data: [ {
    _id: 'stream id',
    name: 'stream name',
    roles: [Array responsible users],
    threadStatuses: [Array statuses],
    visibility: [],
    seenBy: {},
    settings: [{
      widgets: {
        DataTime: { on: true, options: 'deadline', type: 'DataTime' },
        Priority: { on: true, type: 'Priority' },
        Responsible: { on: true, type: 'Responsible' },
        WorkflowStatus: { on: true, type: 'WorkflowStatus' },
        StreamSelect: { on: true, type: 'StreamSelect' },
        Customers: { type: 'Customers', on: true },
        Points: { type: 'Points', on: true }
      },
      notify: {}
    }],
    teamId: 'team id',
    index: 1516360789475,
    owner: 'id creator stream',
    isPrivate: true,
    createdAt: 1516360789475,
    updatedAt: 1516360789475,
    admins: [id admin list]
  } ]
```


# Stream set name
```api.workonflow.com/{teamid}/stream.name/set/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| name       | string       | new name for stream  |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  name: 'New name for stream'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream set admin
```api.workonflow.com/{teamid}/stream.member/setadmin/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| userId       | string       | uniq id of user  |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  userId: '5b0525134c0319001573426a'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |    |


# Stream revoke admin
```api.workonflow.com/{teamid}/stream.member/revokeadmin/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| userId       | string       | uniq id of user  |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  userId: '5b1535134c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream add member
```api.workonflow.com/{teamid}/stream.member/add/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| userId       | string       | uniq id of user  |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  userId: '5b0635434c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |   |


# Stream remove member
```api.workonflow.com/{teamid}/stream.member/remove/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| userId       | string       | uniq id of user  |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  userId: '5b0534256c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream set description
```api.workonflow.com/{teamid}/stream.description/set/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| content       | string       | some text for description |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  content: 'new description for stream'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream get description
```api.workonflow.com/{teamid}/stream.description/get/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |

### Query example:
```
  streamId: '5b0525134c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return description stream object. See example below  |


# Stream create status
```api.workonflow.com/{teamid}/stream.status/create/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| name          | string        | new name for status   |
| streamId       | string       | uniq id of stream  |
| type          | string        | on of the types: Wait, In Progress, Done|
| color         | string        | Color of status in the format: #c0c0c0 |

### Query example:
```
  name: 'New name status',
  streamId: '5b0525134c0319001573485e',
  type: 'In Progress,
  color: '#c0c0c0
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return new id status  |


# Stream get status
```api.workonflow.com/{teamid}/stream.status/get/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream (optionally)   |
| statusId       | string       | uniq id of status |

### Query example:
```
  streamId: '5b0525134c0319001573485e',
  statusId: '5b0525134c0319001573456s'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return status object. See example below  |

```
  data: [ {
    color: "status color in format #c0c0c0",
    name: "name status",
    streamId: "id stream",
    teamId: "id team",
    type: "global status Wait, In progress or Done",
    workflow: "",
    _id: "status id"
  }, {
    // если запрос был по streamId то тут будут перечисленны все статусы
  }, {
    ...
  }]
```


# Stream set name status
```api.workonflow.com/{teamid}/stream.status/setname/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| statusId          | string        | uniq id of status   |
| name       | string       | new name for status |

### Query example:
```
  statusId: '5b0525134c0319001573456s'
  name: 'New name status for current status',
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  return status object. See example below  |

```
  data: [ {
    color: "status color in format #c0c0c0",
    name: "name status",
    streamId: "id stream",
    teamId: "id team",
    type: "global status Wait, In progress or Done",
    workflow: "",
    _id: "status id"
  }]
```


# Stream delete status
```api.workonflow.com/{teamid}/stream.status/delete/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| statusId       | string       | uniq id of status |

### Query example:
```
  streamId: '5b0526a34c0319001573456s',
  statusId: '5b0525134c0319001573456s'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream set field
```api.workonflow.com/{teamid}/stream.field/set/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| budget       | boolean       | on/off field (optionally) |
| deadline       | boolean       | on/off field (optionally) |
| priority       | boolean       | on/off field (optionally) |
| points       | boolean       | on/off field (optionally) |
| timetoc       | boolean       | on/off field (optionally) |

### Query example:
```
  streamId: '5b0526a34c0319001573456s',
  budget: false,
  deadline: false,
  priority: true,
  points: false,
  timetoc: false
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |


# Stream set channel as default
```api.workonflow.com/{teamId}/stream.channels/usedefault/{query}```

### Query:
|               |               |                       |
| ------------- |---------------| ----------------------:|
| streamId          | string        | uniq id of stream   |
| channelId       | string       | uniq id of channel |

### Query example:
```
  streamId: '5b0526a34c0319001573456s',
  channelId: '5b1635134c0319001573456s'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        |  |