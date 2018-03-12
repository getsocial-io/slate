# Public API

## 1. Total shares

```shell
curl "analytics.getsocial.io/api/public/abcd1234/stories/efgh5678/counters/shares/total"
```

> The above command returns a JSON structured like this:

```json
{
  "facebook": 14,
  "twitter": 5,
  "addressbar": 40,
}
```

This endpoint retrieves the total shares for a specific website story, for all-time.


### HTTP Request

`GET http://analytics.getsocial.io/api/public/site_id/stories/story_id/counters/shares/total`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
site_id   | `string` | -            | Website identifier
story_id  | `string` | -            | Story identifier


### Returns

Object with total number of shares per channel present.

