# Public API

## 1. Total shares

```shell
curl "analytics.getsocial.io/api/public/stories/efgh5678/counters/total"
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

`GET http://analytics.getsocial.io/api/public/stories/story_id/counters/total`

### Query Parameters

Parameter | Type     | Default      | Description
--------- | -------- | ------------ | --------
story_id  | `string` | -            | Story identifier


### Returns

Object with total number of shares per channel present.

