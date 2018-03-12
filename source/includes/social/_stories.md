## 3. Stories

### 3.1. Top Stories

```shell
curl "analytics.getsocial.io/api/social/stories/top?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "75dfd2a4fb79",
    "visits": 123,
    "shares": 40,
    "referrals": 150
  },
  {
    "id": "f15a173dd497",
    "visits": 190,
    "shares": 51,
    "referrals": 40
  }
]
```

This endpoint retrieves the overall top stories, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/stories/top`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort stories, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of top stories with total visits, shares and referrals.


### 3.2. Top Stories in last 24-hours

```shell
curl "analytics.getsocial.io/api/stories/top?limit=3&sort_by=referrals"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "75dfd2a4fb79",
    "path": "/lyfestyle/article-z",
    "title": "Article z",
    "shares": 40,
    "referrals": 150
  },
  {
    "id": "f15a173dd497",
    "path": "/sport/article-x",
    "title": "Article x",
    "shares": 51,
    "referrals": 40
  },
  {
    "id": "5f341a5d899a",
    "path": "/sport/article-y",
    "title": "Article y",
    "shares": 100,
    "referrals": 122
  }
]
```

This endpoint retrieves the top stories in the last 24 hours sorted by a specific metric. It can be used to retrieve the most shared or most referred stories.

#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | --------- | --------
limit     | `number` | 10 | Number of stories to be retrieved
sort_by   | `string` | shares | Metric used to sort stories. Accepted values are `shares` and `referrals`


#### Returns

List of stories sorted by `sort_by`.


### 3.3. Fetch Story

```shell
curl "analytics.getsocial.io/api/social/stories/abcd1234?from=2018-01-01&to=2018-01-31"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "identifier": "abcd1234",
  "visits": 213,
  "shares": 40,
  "referrals": 150
}
```

This endpoint retrieves the story information with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/stories/story_id`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data


#### Returns

Story with total visits, shares and referrals.


### 3.4. Fetch Story (legacy)

```shell
curl "analytics.getsocial.io/api/stories/abcd1234?from=2018-01-01&to=2018-01-31"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "identifier": "abcd1234",
  "path": "/lyfestyle/article-z",
  "title": "Article z",
  "shares": 40,
  "referrals": 150
}
```

This endpoint retrieves the story with total shares and referrals between the two dates specified.


#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/story_id`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | ---------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start grouping data
to        | `string` | -            | Date to which to stop grouping data


#### Returns

Story with total shares and referrals.


### 3.5. Top Story Users


```shell
curl "analytics.getsocial.io/api/social/stories/abcd1234/users?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
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

This endpoint retrieves the top users for the story, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/stories/story_id/users`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort top users, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of story top users with total visits, shares and referrals.

### 3.6. Top Story Channels


```shell
curl "analytics.getsocial.io/api/social/stories/abcd1234/channels?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2"
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "facebook",
    "visits": 113,
    "shares": 21,
    "referrals": 64
  },
  {
    "identifier": "twitter",
    "visits": 81,
    "shares": 18,
    "referrals": 72
  }
]
```

This endpoint retrieves the top channels for the story, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/social/stories/story_id/channels`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort top channels, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

List of story top channels with total visits, shares and referrals.