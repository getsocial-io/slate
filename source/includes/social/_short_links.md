## 8. Short Links

###<a id="create-link"></a> 8.1. Create new short link

```shell
curl -X POST "analytics.getsocial.io/api/links" \
  -H "Authorization: abcdef0123abcdef0123"
  -H "Content-Type: application/x-www-form-urlencoded" \
  --data-urlencode "url=http://example.com/path"
```

> The above command returns a JSON structured like this:

```json
{
  "result": "ok",
  "link": "https://api.at.getsocial.io/abcdef",
  "id": "123456"
}
```

This endpoint creates a new short link, given a URL belonging to your website. You can later find it
also on your GetSocial dashboard.


#### HTTP Request

`POST http://analytics.getsocial.io/api/links`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
url       | `string` | -            | URL to shorten; must include website domain and protocol


#### Response fields

Field        | Type      | Description
------------ | --------- | --------
result       | `string`  | Whether call was successful. Is `ok` or `err`, in case of error
id           | `string`  | The short link ID
link         | `string`  | The short link created

### 8.2. Get link statistics

```shell
curl "analytics.getsocial.io/api/links/abcdef?from=2020-01-20" \
  -H "Authorization: abcdef0123abcdef0123"
```

> The above command returns a JSON structured like this:

```json
{
  "sequence": {
    "referrals": [],
    "earned": [],
    "total_traffic": []
  },
  "totals": {
    "referrals": 0,
    "earned": 0,
    "total_traffic": 0,
    "shares": 0,
    "uplift": 0
  },
  "channels":{
    "Dark Social": {
      "referrals": 0,
      "shares": 0,
      "earned": 0,
      "total_traffic": 0,
      "viral_uplift": 0
    }
  }
}
```

This endpoint retrieves all data, optionally since the date specified (subject to the website timezone).
 If the date is the current date, the `sequence` field shows hourly data, otherwise it shows daily data.

The short link ID is required. You can find it in the response from <a href="#create-link">the previous endpoint</a>, or in your GetSocial dashboard. For instance at https://getsocial.io/sites/your-website-com/link-detail/LINK_ID.

#### HTTP Request

`GET http://analytics.getsocial.io/api/api/<link_id>`

#### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
from      | `string` | -            | Date from which to start retrieving data, in `2020-08-20` format


#### Response fields

Field    | Type   | Description
-------- | ------ | --------
sequence | `hash` | Referrals, earned visits and total traffic, discriminated by day or hour
totals   | `hash` | Total statistics for the time period
channels | `hash` | Statistics by channel for the time period
