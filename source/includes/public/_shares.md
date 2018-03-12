# Public API

## 1. Total shares


```shell
curl "analytics.getsocial.io/api/abc123/public/counters/shares/total"
```

> The above command returns a JSON structured like this:

```json
{
  "facebook": 14,
  "twitter": 5,
  "addressbar": 40,
}
```

This endpoint retrieves the total shares for the website, for all-time.


### HTTP Request

`GET http://analytics.getsocial.io/api/site_id/public/counters/shares/total`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
site_id   | `string` | -            | Website identifier


### Returns

Object with total number of shares per channel present.

