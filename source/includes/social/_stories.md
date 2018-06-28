## 3. Stories

### 3.1. Top Stories

```shell
curl "analytics.getsocial.io/api/stories/top?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "75dfd2a4fb79",
    "visits": 123,
    "shares": 40,
    "referrals": 150,
    "title": "The Precipice",
    "path": "/"
  },
  {
    "id": "f15a173dd497",
    "visits": 190,
    "shares": 51,
    "referrals": 40,
    "title": "The Frigate Pallada",
    "path": "/"
  }
]
```

This endpoint retrieves the overall top stories, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/top`

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
curl "analytics.getsocial.io/api/stories/top?limit=3&sort_by=referrals" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "75dfd2a4fb79",
    "path": "/lyfestyle/article-z",
    "title": "Article z",
    "visits": 100,
    "shares": 40,
    "referrals": 150
  },
  {
    "id": "f15a173dd497",
    "path": "/sport/article-x",
    "title": "Article x",
    "visits": 60,
    "shares": 51,
    "referrals": 40
  },
  {
    "id": "5f341a5d899a",
    "path": "/sport/article-y",
    "title": "Article y",
    "visits": 150,
    "shares": 100,
    "referrals": 122
  }
]
```

This endpoint retrieves the top stories in the last 24 hours sorted by a specific metric. It can be used to retrieve the most shared, most referred or most visited stories.

#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | --------- | --------
limit     | `number` | 10 | Number of stories to be retrieved
sort_by   | `string` | shares | Metric used to sort stories. Accepted values are `visits`, `shares` and `referrals`


#### Returns

List of stories sorted by `sort_by`.


### 3.3. Fetch Story

```shell
curl "analytics.getsocial.io/api/stories/abcd1234?from=2018-01-01&to=2018-01-31" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "identifier": "abcd1234",
  "title": "De Petersburgse pest",
  "path": "/",
  "visits": 213,
  "shares": 40,
  "referrals": 150,
  "viral_score": 27.85,
  "sharing_rate": 6.25
}
```

This endpoint retrieves the story information with total visits, shares, referrals, share rate and viral score between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/story_id`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data


#### Returns

Story with total visits, shares and referrals.


### 3.4. Fetch Story Identifier


```shell
curl "analytics.getsocial.io/api/stories/resolve_id/?path=/article-104" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "identifier": "efgh5678"
}
```

This endpoint retrieves the story identifier that identifies a story, given it's path.

The path must be clean of query arguments and hashtags, and should be CGI/HTML form encoded, although
an attempt is made to understand misencoded paths. For example for the URL `http://example.com/path/site.htm?arg=1#top` the path should be `%2Fpath%2Fsite.htm`.


#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/resolve_id`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
path      | `string` | -       | Story path


#### Returns

Story identifier.


### 3.5. Top Story Users


```shell
curl "analytics.getsocial.io/api/stories/abcd1234/users?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "identifier": "friend@gmail.com",
    "visits": 113,
    "shares": 21,
    "referrals": 64,
    "title": "Ninfodora Ivánovna",
    "path": "/goncharov/h/310/web.php"
  },
  {
    "identifier": "enemy@gmail.com",
    "visits": 81,
    "shares": 18,
    "referrals": 72,
    "title": "Fathers and Sons",
    "path": "/page-12/1423523/fathers-and-sons-1"
  }
]
```

This endpoint retrieves the top users for the story, with total visits, shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/story_id/users`

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
curl "analytics.getsocial.io/api/stories/abcd1234/channels?from=2018-01-01&to=2018-01-3&sort_by=shares&limit=2" \
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

`GET http://analytics.getsocial.io/api/stories/story_id/channels`

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
