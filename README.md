## Workonflow bot rest api ##

### Введение

**API** — это интерфейс для управления каким-либо программным обеспечением извне. Подобное управление осуществляется с помощью набора готовых классов, процедур и функций. Зачастую API используют для интеграции одного сервиса с другим.

**API Workonflow bot** - это возможности взаимодействия с панелью [workonflow](workonflow.com) через бота.

**Бот** - специальная программа, выполняющая автоматически и/или по заданному расписанию какие-либо действия через интерфейсы, предназначенные для людей. 

***Вот лишь небольшой перечень его возможных применений:***
- создание потоков статусов и задач
- обновление настроек задач
- отправка сообщений пользователям
- создание комментариев в потоке или задаче

Обмен сообщениями идёт по обыкновенной HTTP  схеме «запрос-ответ».

**HTTP** — это протокол, не нуждающийся в представлении, ведь даже эта страница передана на ваш компьютер с помощью него ([wikipedia](https://ru.wikipedia.org/wiki/HTTP)).

Мы будем постоянно добавлять новые API-методы, чтобы покрыть все ваши потребности в автоматизации работы [workonflow](workonflow.com). Если нужный функционал ещё не представлен в API, напишите нам. Наиболее востребованные методы будут реализованы в первую очередь.

---

### Начало работы

Каждый запрос к **API** должен быть авторизован.

Авторизация - это процес подтверждения подлинности запроса и разрешение на его выполнение.

Прежде всего для авторизации запроса требуется пара значений **apikey**, **secretkey** и **signature**.

**apikey** - это приватный ключ для формирования сигнатуры запросов. Получить apikey можно на странице создания ботов [console.workonflow.com](https://console.workonflow.com), в разделе настроек запросов. Он уникальный для каждого бота.

**secretkey** - это приватный ключ так-же необходимый для формирования сигнатуры запросов. Получить его можно на главной странице создания ботов [console.workonflow.com](https://console.workonflow.com)

**signature** - это подпись, закодированный параметр, который необходимо передать в заголовке "X-Signature"

Для того чтобы создать **signature** вам необходимо создать хэш sha256 в формате Hex, из **apikey** + **secretkey** + timestamp в секундах

**Пример создания signature:**
```js
  sha256Hex(apikey + secretkey + timestampInSeconds)
```

> **Важно!** При **каждом** запросе обязательно необходимо предавать следующие зоголовки:

|Название заголовка| Значение |
|-----|-----|
|Api-key| Your registered API key |
|X-Signature| SHA256 encoding signature |

В случае если параметры не будут переданны или один из ключей не верный, ваш запрос будет неудачен, и вы получите ошибку HTTP 403.

### Общие правила запросов

События и ответы на запросы используют самый популярный формат json.

Если ваши запросы получают данные, которые можно кэшировать на некоторое время, вам следует их кэшировать, чтобы не запрашивать одни и те же данные многократно.

Чтобы отправить запрос, нужно использовать идентификаторы или «URI». URL любого API-запроса составляется следующим образом:

```js
  https://api.workonflow.com/{teamId}/{URI}?{query}
```

где
- *teamId* - идентификатор тимы
- *URI* - универсальный идентификатор ресурса
- *query* - параметры запроса

К примеру что бы получить информацию по стриму, запрос должен быть следующим:

```js
  https://api.workonflow.com/5b4484384e3e54001e267ed8/stream/read?query={"streamId":"7b4484384e3454001egh7847"}
```

#### Методы передачи параметров запроса

|Метод|Назначение|
|--- |---|
|POST|Добавление новых данных|
|GET |Получение существующих данных|

-----

### Таблица событий и действий панели Workonflow

|Название| Возможные действия    |  Возможные события          |
|-----|:-----:|:------------:|
| **channel** | [actions](./request/channel.md) |              |
| **call**    | [actions](./request/call.md)    | [events](./events/call.md) |
| **comment** | [actions](./request/comment.md) | [events](./events/comment.md)|
| **contact** | [actions](./request/contact.md) |              |
| **file**    | [actions](./request/file.md)    |              |
| **stream**  | [actions](./request/stream.md)  | [events](./events/stream.md) |
| **team**    | [actions](./request/team.md)    | [events](./events/team.md)   |
| **thread**  | [actions](./request/thread.md)  | [events](./events/thread.md) |
