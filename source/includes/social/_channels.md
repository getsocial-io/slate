## 4. Channels

### 4.1. Top Channels

```shell
curl "analytics.getsocial.io/api/channels/top?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "Facebook",
    "shares": 40,
    "referrals": 150
  },
  {
    "identifier": "Twitter",
    "shares": 9,
    "referrals": 12
  }
]
```

This endpoint retrieves the overall top channels, with total shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/channels/top`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort channels, can be `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of top channels with total shares and referrals.


### 4.2. Top Channels in last 24-hours

```shell
curl "analytics.getsocial.io/api/channels/top?limit=3&sort_by=referrals" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "Facebook",
    "shares": 40,
    "referrals": 150
  },
  {
    "identifier": "Twitter",
    "shares": 10,
    "referrals": 80
  },
  {
    "identifier": "CopyPaste",
    "shares": 10,
    "referrals": 30
  }
]
```

This endpoint retrieves the top stories in the last 24 hours sorted by a specific metric. It can be used to retrieve the most shared, most referred or most visited stories.

#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | --------- | --------
limit     | `number` | 10 | Number of channels to be retrieved
sort_by   | `string` | shares | Metric used to sort channels. Accepted values are `shares` and `referrals`


#### Returns

List of channels sorted by `sort_by`.


### 4.3. Top Channel Users


```shell
curl "analytics.getsocial.io/api/channels/facebook/users?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "friend@gmail.com",
    "visits": 113,
    "shares": 21,
    "referrals": 64
  },
  {
    "identifier": "enemy@gmail.com",
    "visits": 81,
    "shares": 18,
    "referrals": 72
  }
]
```

This endpoint retrieves the top users for the channel, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/channels/channel_id/users`

#### Query Parameters

Parameter  | Type     | Default      | Description
---------- | -------- | ------------ | --------
channel_id | `string` | -            | Channel identifier
from       | `string` | -            | Date from which to start counting data
to         | `string` | -            | Date to which to stop counting data
sort_by    | `string` | `shares`     | Criteria by which to sort users, can be `visits`, `shares` or `referrals`
limit      | `number` | 10           | Max number of results to retrieve


#### Returns

List of channel top users with total visits, shares and referrals.

<!--
### 4.4. Top Channel Stories


```shell
curl "analytics.getsocial.io/api/channels/facebook/stories?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "abcd1234",
    "visits": 113,
    "shares": 21,
    "referrals": 64,
    "title": "The Same Old Story",
    "path": "/"
  },
  {
    "identifier": "abcd1235",
    "visits": 81,
    "shares": 18,
    "referrals": 72,
    "title": "Oblomov",
    "path": "/home"
  }
]
```

This endpoint retrieves the top stories for the channel, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/channels/channel_id/stories`

#### Query Parameters

Parameter  | Type     | Default      | Description
---------- | -------- | ------------ | --------
channel_id | `string` | -            | Channel identifier
from       | `string` | -            | Date from which to start counting data
to         | `string` | -            | Date to which to stop counting data
sort_by    | `string` | `shares`     | Criteria by which to sort stories, can be `visits`, `shares` or `referrals`
limit      | `number` | 10           | Max number of results to retrieve


#### Returns

List of channel top stories with total visits, shares and referrals.
-->
