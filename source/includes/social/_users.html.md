## 2. Users

### 2.1. Top Users

```shell
curl "analytics.getsocial.io/api/social/users/top?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
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


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/users/top`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort users, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of top users with total visits, shares and referrals.


### 2.2. Fetch User

```shell
curl "analytics.getsocial.io/api/social/users/friend%40gmail.com?from=2018-01-01&to=2018-01-31"
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


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/users/user_id`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
user_id   | `string` | -            | User identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data


### Returns

User with total visits, shares and referrals.


### 2.3. Top User Stories

```shell
curl "analytics.getsocial.io/api/social/users/friend%40gmail.com/stories?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "abcd1234",
    "visits": 5,
    "shares": 40,
    "referrals": 150,
    "title": "First Love",
    "path": "/first-love/40100ff-0"
  },
  {
    "identifier": "abcd1235",
    "visits": 31,
    "shares": 9,
    "referrals": 12,
    "title": "Home of the Gentry",
    "path": "/index.htm"
  }
]
```

This endpoint retrieves the top stories for the user, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/users/channel_id/stories`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
user_id   | `string` | -            | User identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort stories, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of user top stories with total visits, shares and referrals.


### 2.4. Top User Channels

```shell
curl "analytics.getsocial.io/api/social/users/friend%40gmail.com/channels?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
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


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/users/channel_id/channels`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
user_id   | `string` | -            | User identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort channels, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of user top channels with total visits, shares and referrals.



