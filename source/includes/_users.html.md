# 3. Users

## 3.1. Top Users

```shell
curl "analytics.getsocial.io/api/v1/users/top?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "friend@gmail.com",
    "visits": 5,
    "shares": 40,
    "referrals": 150
  },
  {
    "identifier": "enemy@gmail.com",
    "visits": 31,
    "shares": 9,
    "referrals": 12
  }
]
```

This endpoint retrieves the overall top users, with total visits, shares and referrals between the two dates specified (inclusive).


### HTTP Request

`GET http://analytics.getsocial.io/api/v1/users/top`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort users, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


### Returns

List of top users with total visits, shares and referrals.


## 3.2. Fetch User

```shell
curl "analytics.getsocial.io/api/v1/users/friend%40gmail.com?from=2018-01-01&to=2018-01-31"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "identifier": "friend@gmail.com",
  "visits": 213,
  "shares": 40,
  "referrals": 150
}
```

This endpoint retrieves the user information with total visits, shares and referrals between the two dates specified (inclusive).


### HTTP Request

`GET http://analytics.getsocial.io/api/v1/users/user_id`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
user_id   | `string` | -            | User identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data


### Returns

User with total visits, shares and referrals.


## 3.3. Top User Stories

```shell
curl "analytics.getsocial.io/api/v1/users/friend%40gmail.com/stories?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "abcd1234",
    "path": "/lyfestyle/article-z",
    "title": "Article z",
    "visits": 5,
    "shares": 40,
    "referrals": 150
  },
  {
    "identifier": "abcd1235",
    "path": "/lyfestyle/article-x",
    "title": "Article x",
    "visits": 31,
    "shares": 9,
    "referrals": 12
  }
]
```

This endpoint retrieves the top stories for the user, with total visits, shares and referrals between the two dates specified (inclusive).


### HTTP Request

`GET http://analytics.getsocial.io/api/v1/users/channel_id/stories`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
user_id   | `string` | -            | User identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort stories, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


### Returns

List of user top stories with total visits, shares and referrals.


## 3.4. Top User Channels

```shell
curl "analytics.getsocial.io/api/v1/users/friend%40gmail.com/channels?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "facebook",
    "visits": 81,
    "shares": 40,
    "referrals": 150
  },
  {
    "identifier": "twitter",
    "visits": 12,
    "shares": 9,
    "referrals": 12
  }
]
```

This endpoint retrieves the top channels for the user, with total visits, shares and referrals between the two dates specified (inclusive).


### HTTP Request

`GET http://analytics.getsocial.io/api/v1/users/channel_id/channels`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
user_id   | `string` | -            | User identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort channels, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


### Returns

List of user top channels with total visits, shares and referrals.



