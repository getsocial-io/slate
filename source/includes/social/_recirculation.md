## 7. Recirculation

On GetSocial, we measure recirculation of articles that were visited from a share.

### 7.1. Top recirculations by Story

```shell
curl "analytics.getsocial.io/api/stories/abcd1234/recirculation/top?limit=2&from=2018-01-01&to=2018-01-31" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "path": "/",
    "identifier": "abcd1234",
    "title": "Lifestyle Global",
    "count": "44012"
  },
  {
    "path": "/7-dieting-tips",
    "identifier": "aceg1357",
    "title": "Our top 7 dieting tips",
    "count": "1023"
  }
]
```

This endpoint retrieves the most recirculated stories from the origin story specified by story ID.

#### HTTP Request

`GET http://analytics.getsocial.io/api/stories/<story_id>/recirculation/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
story_id  | `string` | -       | Story ID
from      | `string` | -       | Date from which to start counting data; is required
to        | `string` | -       | Date to which to stop counting data; is required
limit     | `number` | 10      | Max number of results to retrieve; 100 is the hard limit by request

#### Returns

List of top recirculations, with times visited from origin story.

### 7.2. Top recirculations by Channel

```shell
curl "analytics.getsocial.io/api/channels/facebook/recirculation/top?limit=2&from=2018-01-01&to=2018-01-31" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "path": "/",
    "identifier": "abcd1234",
    "title": "Lifestyle Global",
    "count": "45617"
  },
  {
    "path": "/7-dieting-tips",
    "identifier": "aceg1357",
    "title": "Our top 7 dieting tips",
    "count": "987"
  }
]
```

This endpoint retrieves the most recirculated stories from shares from a specific channel.

#### HTTP Request

`GET http://analytics.getsocial.io/api/channels/<channel>/recirculation/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
channel   | `string` | -       | Channel ID, like `facebook` or `twitter`
from      | `string` | -       | Date from which to start counting data; is required
to        | `string` | -       | Date to which to stop counting data; is required
limit     | `number` | 10      | Max number of results to retrieve; 100 is the hard limit by request

#### Returns

List of top recirculations, with times visited from origin channel.

### 7.3. Top recirculations

```shell
curl "analytics.getsocial.io/api/recirculation/top?limit=2&from=2018-01-01&to=2018-01-31" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
[
  {
    "path": "/",
    "identifier": "abcd1234",
    "title": "Lifestyle Global",
    "count": "301980"
  },
  {
    "path": "/7-dieting-tips",
    "identifier": "aceg1357",
    "title": "Our top 7 dieting tips",
    "count": "32134"
  }
]
```

This endpoint retrieves the most recirculated to stories, from origin referrals based on the bellow
criteria.

#### HTTP Request

`GET http://analytics.getsocial.io/api/recirculation/top`

#### Query Parameters

Parameter | Type     | Default | Description
--------- | -------- | ------- | --------
story_id  | `string` | -       | Story ID; is optional
channel   | `string` | -       | Channel ID, like `facebook` or `twitter`; is optional
from      | `string` | -       | Date from which to start counting data; is required
to        | `string` | -       | Date to which to stop counting data; is required
limit     | `number` | 10      | Max number of results to retrieve; 100 is the hard limit by request

#### Returns

List of top recirculations, with times visited.
