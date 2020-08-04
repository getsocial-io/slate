## 3. Stories

### <a id="top-stories"></a>3.1. Top Stories

```shell
curl "https://analytics.getsocial.io/api/stories/top?from=2018-01-01&to=2018-01-31&sort_by=shares&limit=2" \
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
    "sharing_rate": 35.52,
    "viral_score": 75.23,
    "recirculation_percentage": 3.4,
    "recirculation_depth": 2.43,
    "title": "The Precipice",
    "path": "/"
  },
  {
    "identifier": "f15a173dd497",
    "visits": 190,
    "shares": 51,
    "referrals": 40,
    "sharing_rate": 26.84,
    "viral_score": 5.23,
    "recirculation_percentage": 4.3,
    "recirculation_depth": 4.21,
    "title": "The Frigate Pallada",
    "path": "/",
    "cursor_id": "f15a173dd497_51"
  }
]
```

This endpoint retrieves the overall top stories, with total visits, shares, referrals, share rate, virality score and recirculation between the two dates specified (inclusive).


#### HTTP Request

`GET https://analytics.getsocial.io/api/stories/top`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort stories, can be `visits`, `shares`, `referrals`, `sharing_rate`, `viral_score`, `recirculation_percentage` or `recirculation_depth`
limit     | `number` | 10           | Max number of results to retrieve
starting_after | `string` | -           | A cursor for use in pagination, an object ID that defines the place in the list. For instance, if you make a list request and receive 10 objects, ending with `cursor_id=f15a173dd497_51`, your subsequent call can include `starting_after=f15a173dd497_51` in order to fetch the next page of the list. The `cursor_id` value is available in the last returned story.

#### Returns

Field        | Type      | Description
------------ | --------- | --------
-            | <a href="#story-returns">`Story[]`</a>  | Top stories

### 3.2. Top Stories in last 24-hours

```shell
curl "https://analytics.getsocial.io/api/stories/top?limit=3&sort_by=referrals" \
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
    "sharing_rate": 40.0,
    "viral_score": 30.04,
    "recirculation_percentage": 3.4,
    "recirculation_depth": 2.42,
    "referrals": 150
  },
  {
    "identifier": "f15a173dd497",
    "path": "/sport/article-x",
    "title": "Article x",
    "visits": 60,
    "shares": 51,
    "sharing_rate": 85.0,
    "viral_score": 10.32,
    "recirculation_percentage": 4.3,
    "recirculation_depth": 4.29,
    "referrals": 40
  },
  {
    "identifier": "5f341a5d899a",
    "path": "/sport/article-y",
    "title": "Article y",
    "visits": 150,
    "shares": 100,
    "sharing_rate": 66.67,
    "viral_score": 2.19,
    "recirculation_percentage": 5.4,
    "recirculation_depth": 1.03,
    "referrals": 122
  }
]
```

This endpoint retrieves the top stories in the last 24 hours sorted by a specific metric. It can be used to retrieve the most shared, most referred, most visited, most viral stories or most recirculated stories.

#### HTTP Request

`GET https://analytics.getsocial.io/api/stories/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | --------- | --------
limit     | `number` | 10 | Number of stories to be retrieved
sort_by   | `string` | `shares`     | Criteria by which to sort stories, can be `visits`, `shares`, `referrals`, `sharing_rate`, `viral_score`, `recirculation_percentage` or `recirculation_depth`


#### Returns

Field        | Type      | Description
------------ | --------- | --------
-            | <a href="#story-returns">`Story[]`</a>  | Top stories


### 3.3. Fetch Story

```shell
curl "https://analytics.getsocial.io/api/stories/abcd1234?from=2018-01-01&to=2018-01-31&with_channels=true" \
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
  "sharing_rate": 6.25,
  "recirculation_percentage": 12.3,
  "recirculation_depth": 4.32,
  "channels": {
    "DarkSocial": {"shares": 10, "referrals": 120, "viral_score": 3.05, "recirculation_percentage": 1.2, "recirculation_depth": 4},
    "Facebook": {"shares": 30, "referrals": 30, "viral_score": 5.05, "recirculation_percentage": 2.2, "recirculation_depth": 4},
  }
}
```

This endpoint retrieves the story information with total visits, shares, referrals, share rate and virality score between the two dates specified (inclusive).


#### HTTP Request

`GET https://analytics.getsocial.io/api/stories/<story_id>`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier. In case you want to lookup by path instead of identifier, set the `query` parameter with the path encoded. In that case, set `story_id` as `id`
query     | `string` | -            | The parameter is optional but in case of present the story will be queried via the value given by this parameter instead of the value given by `story_id`
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
with_channels | `boolean` | false   | In case of `true` the analytics data for each channel is also provided

<h4 id="story-returns">Returns</h4>

Field                    | Type      | Description
------------             | --------- | --------
identifier               | `string`  | The story identifier
visits                   | `integer` | Number of visits to the story
shares                   | `integer` | Number of shares performed on the story
referrals                | `integer` | Number of visits generated by user's shared posts relative to this story
sharing_rate             | `float`   | Rate of users sharing the story
recirculation_percentage | `float`   | Percentage of recirculations from referrals
recirculation_depth      | `float`   | Average depth of recirculations from referrals
viral_score              | `float`   | Organic virality index of the story
title                    | `string`  | The story title
path                     | `string`  | The story URL path


### 3.4. Fetch Story Identifier


```shell
curl "https://analytics.getsocial.io/api/stories/resolve_id/?path=/article-104" \
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

`GET https://analytics.getsocial.io/api/stories/resolve_id`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
path      | `string` | -       | Story path


#### Returns

Field        | Type      | Description
------------ | --------- | --------
identifier   | `string`  | The story identifier


### 3.5. Top Story Users


```shell
curl "https://analytics.getsocial.io/api/stories/abcd1234/users?from=2018-01-01&to=2018-01-31&sort_by=shares&limit=2" \
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

`GET https://analytics.getsocial.io/api/stories/<story_id>/users`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data
sort_by   | `string` | `shares`     | Criteria by which to sort top users, can be `visits`, `shares` or `referrals`
limit     | `number` | 10           | Max number of results to retrieve


#### Returns

Field        | Type      | Description
------------ | --------- | --------
identifier   | `string`  | The user identifier
visits       | `integer` | Number of visits to the story by the user
shares       | `integer` | Number of shares performed on the story by the user
referrals    | `integer` | Number of visits generated by the user's shared posts relative to this story
title        | `string`  | The story title
path         | `string`  | The story URL path

<!--
### 3.6. Top Story Channels


```shell
curl "https://analytics.getsocial.io/api/stories/abcd1234/channels?from=2018-01-01&to=2018-01-31&sort_by=shares&limit=2" \
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

`GET https://analytics.getsocial.io/api/stories/story_id/channels`

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
-->

### 3.6. Top recirculation destinations

On GetSocial, we measure recirculation of articles that were visited from a share. This endpoint retrieves the most recirculated to stories (destination stories).

If you instead need the top stories or channels by own recirculation please see endpoints <a href="#top-stories">3.1. Top Stories</a> and <a href="#top-channels">5.1. Top Channels</a>, with a sort criteria of recirculation.

```shell
curl "https://analytics.getsocial.io/api/stories/top/recirculated_to?limit=2&from=2018-01-01&to=2018-01-31" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "path": "/",
    "identifier": "abcd1234",
    "title": "Lifestyle Global",
    "count": 301980
  },
  {
    "path": "/7-dieting-tips",
    "identifier": "aceg1357",
    "title": "Our top 7 dieting tips",
    "count": 32134
  }
]
```

#### HTTP Request

`GET https://analytics.getsocial.io/api/stories/top/recirculated_to`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
story_id  | `string` | -       | Source Story ID; is optional
channel   | `string` | -       | Source Channel ID, like `facebook` or `twitter`; is optional
from      | `string` | -       | Date from which to start counting data; is required
to        | `string` | -       | Date to which to stop counting data; is required
limit     | `number` | 10      | Max number of results to retrieve; 100 is the hard limit by request

#### Returns

List of top recirculated to stories, with times visited.


### 3.7. Top Story Locations


```shell
curl "https://analytics.getsocial.io/api/stories/abcd1234/locations?from=2018-01-01&to=2018-01-31&sort_by=shares" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "country_code": "PT",
    "region": "Lisboa",
    "shares": 3500,
    "referrals": 1500
  },
  {
    "country_code": "PT",
    "region": "Porto",
    "shares": 3000,
    "referrals": 2345
  },
  {
    "country_code": "ES",
    "region": "Madrid",
    "shares": 2670,
    "referrals": 1500
  }
]
```

This endpoint retrieves the top locations for the story, with total shares and referrals between the two dates specified (inclusive).


#### HTTP Request

`GET https://analytics.getsocial.io/api/stories/<story_id>/locations`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier
from      | `string` | -            | Date from which to start counting data
to        | `string` | -            | Date to which to stop counting data


#### Fields in array response

Field        | Type      | Description
------------ | --------- | --------
country_code | `string`  | The country code on ISO 3166-1 alpha-2 format
region       | `string`  | The region name
shares       | `integer` | Number of shares performed on that region
referrals    | `integer` | Number of visits on that region generated by shared posts
