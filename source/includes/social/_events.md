## 5. Events

### 5.1. List Events

```shell
curl "analytics.getsocial.io/api/events/list?from=2018-01-01&to=2018-01-3&user=1200139&channel=facebook&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "user": "1200139",
    "date": "2018-07-02 15:38:15 +0100",
    "story": "story-id-13411",
    "channel": "facebook",
    "type": "a1b2c3",
    "attributes": {
      "total": "USD 1198.05"
    }
  },
  {
    "user": "1200139",
    "date": "2018-07-02 15:38:05 +0100",
    "story": "story-id-22001",
    "channel": "facebook",
    "type": "d4e5f6",
    "attributes": null
  }
]
```

This endpoint retrieves a complete list of individual conversion events, with the attributes provided
on submission.

#### HTTP Request

`GET http://analytics.getsocial.io/api/events/list`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
from      | `string` | -       | Date from which to start counting data
to        | `string` | -       | Date to which to stop counting data
user      | `string` | -       | Argument with which to refine search
story     | `string` | -       | Argument with which to refine search
channel   | `string` | -       | Argument with which to refine search
type      | `string` | -       | Argument with which to refine search
limit     | `number` | 10      | Max number of results to retrieve; 1000 is the hard limit by request

#### Returns

List of detailed conversion events, ordered by date.


### 5.2. Count Events

```shell
curl "analytics.getsocial.io/api/events/count?story=274819848&type=purchases" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "count": 122
}
```

This endpoint counts the total number of events given the query arguments provided.

#### HTTP Request

`GET http://analytics.getsocial.io/api/events/count`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
from      | `string` | -       | Date from which to start counting data
to        | `string` | -       | Date to which to stop counting data
user      | `string` | -       | Argument with which to refine search
story     | `string` | -       | Argument with which to refine search
channel   | `string` | -       | Argument with which to refine search
type      | `string` | -       | Argument with which to refine search


#### Returns

Total number of elements found.


### 5.3. Count Events By Attribute


```shell
curl "analytics.getsocial.io/api/events/count/channels?from=2018-01-01&to=2018-01-3&user=AmAm1234&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "id": "facebook",
    "count": 31
  },
  {
    "id": "twitter",
    "count": 13
  }
]
```

Counts number of results grouped by an attribute (channel in this example), optionally filtered by user, story channel or event type.

#### HTTP Request

`GET http://analytics.getsocial.io/api/count/<attribute>`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
attribute | `string` | -       | Attribute with which to group event counts (`users`, `stories`, `channels` or `types`)
from      | `string` | -       | Date from which to start counting data
to        | `string` | -       | Date to which to stop counting data
user      | `string` | -       | Argument with which to refine search
story     | `string` | -       | Argument with which to refine search
channel   | `string` | -       | Argument with which to refine search
type      | `string` | -       | Argument with which to refine search
limit     | `number` | 10      | Max number of results to retrieve; 1000 is the hard limit by request


#### Returns

List of events grouped by an attribute, with the corresponding ID per element; sorted by number of results.
