## 4. Channels

### 4.1. Top Channels

```shell
curl "analytics.getsocial.io/api/social/channels/top?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "facebook",
    "visits": 5,
    "shares": 40,
    "referrals": 150
  },
  {
    "identifier": "twitter",
    "visits": 31,
    "shares": 9,
    "referrals": 12
  }
]
```

This endpoint retrieves the overall top channels, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/channels/top`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort channels, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of top channels with total visits, shares and referrals.


### 4.2. Fetch Channel

```shell
curl "analytics.getsocial.io/api/social/channels/facebook?from=2018-01-01&to=2018-01-31"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "identifier": "facebook",
  "visits": 213,
  "shares": 40,
  "referrals": 150
}
```

This endpoint retrieves the channel information with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/channels/channel_id`

#### Query Parameters

Parameter  | Type     | Default      | Description
---------- | -------- | ------------ | --------
channel_id | `string` | -            | Channel identifier
from       | `string` | -            | Date from which to start counting data
to         | `string` | -            | Date to which to stop counting data


#### Returns

Channel with total visits, shares and referrals.


### 4.3. Top Channel Users


```shell
curl "analytics.getsocial.io/api/social/channels/facebook/users?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
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

`GET http://analytics.getsocial.io/api/social/channels/channel_id/users`

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


### 4.4. Top Channel Stories


```shell
curl "analytics.getsocial.io/api/social/channels/facebook/stories?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
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

`GET http://analytics.getsocial.io/api/social/channels/channel_id/stories`

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

