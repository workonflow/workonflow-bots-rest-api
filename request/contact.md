## Support GET and POST HTTP methods

# Метод для создания контакта
```api.workonflow.com/{teamid}/contact/create/{query}```

### Query:
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| basicData     | object        | Takes an object with the name of the contact |
| customFields  | array         | Field for adding channels to the contact  |

### Query example:
```
  basicData: {
    name: "Alex",
    email: "email@email.com"
  },
  customFields: [
    {id: "B1R5NTS3z", label: "Company", value: "", type: "company"},
    {id: "B1l094TB2M", label: "Work phone", value: "", type: "phone"},
    {id: "rkbA9VTH3M", label: "Work e-mail", value: "", type: "email"}
  ]
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return contact id. Example: data: { insertedCount: 1, insertedId: '1491eh1029318du1dqw9' }   |


# Метод для получения "языка" пользователя
```api.workonflow.com/{teamid}/contact/local/{query}```

### Query:
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| userId     | string        | id of user |

### Query example:
```
  userId: '5b0525134c0319001573485e'
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return locale user. Example: data: { locale: 'en' }   |


# Метод для получения пользоватей
```api.workonflow.com/{teamid}/contact/get/{query}```

### Query:
| field         | type          | description|
| ------------- |---------------| ----------------------:|
| userId        | string        | Contact or user ID |
| userIds       | array         | Several contact or user IDs  |

### Query example:
```
  userId: '5b0525134c0319001573485e',
  userIds: ['5afd6d369a88ff00190baf79', '5afd6d369a88ff22190baf79']
```

### RESPONSES:
| code        | message | description|
|:------------- |:---------------|:----------------------|
| 200          | OK        | return user or contact. See example below   |

### user:
```
  data: [ {
    _id: 'user id',
    billingType: 'users',
    basicData: {
      name: 'user name',
      email: [ 'user email' ],
      phone: [ 'user phone' ]
    },
    extension: 'number extension in system',
    canonicalPhone: [],
    teamId: 'team id',
    createdAt: '2017-10-30T10:15:53.245Z',
    updatedAt: 1517574060991,
    color: 'background name color',
    hrData: { position: '' },
    status: 'on||off (online or no)',
    voiceRules: [ {
      type: 'webrtc',
      enabled: true,
      timeout: '',
      extension: '100*9 (default number extension + *9)',
      visible: true
    }, {
      type: 'sip',
      enabled: true,
      timeout: '',
      extension: '100*1 (default number extenseion + *1)',
      visible: true
    } ]
  } ]
```

### external user:
```
  data: [ {
      _id: '5ad848cc014201001f82c947',
      basicData: { name: 'new name customer' },
      customFields:  [ {
        id: 'B1R5NTS3z',
        label: 'Company',
        value: '',
        type: 'company'
      }, {
        id: 'B1l094TB2M',
        label: 'Work phone',
        value: '',
        type: 'phone'
      }, {
        id: 'rkbA9VTH3M',
        label: 'Work e-mail',
        value: '',
        type: 'email'
      } ],
      billingType: 'contacts',
      teamId: '59f6fbd69af753001e453905',
      createdAt: '2018-04-19T07:44:12.942Z',
      updatedAt: '2018-04-19T07:44:12.942Z',
      color: '#718699',
      status: 'off',
      voiceRules: [ {
        type: 'webrtc',
        enabled: true,
        timeout: '',
        extension: '*9',
        visible: true
      }, {
        type: 'sip',
        enabled: true,
        timeout: '',
        extension: '*1',
        visible: true
      } ]
    } ]
```