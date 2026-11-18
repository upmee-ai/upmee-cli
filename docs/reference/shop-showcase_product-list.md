# List Showcase Products

### Request URL

`https://www.upmee.cc/open_api/shop/showcase_product/list`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type.<br>Allowed format: `application/json`. |

### Request Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| team_id | string | Team ID |
| media_id | string | Social account ID |
| count | number | Number of items to retrieve |
| status_filter | string | Product status filter. Supported values:<br>- `ALL`: All<br>- `SHOPPABLE`: Products available for sale<br>- `HIDDEN`: Hidden products<br>- `SOLD_OUT`: Sold out |
| order | string | Sort order. Supported values:<br>- `COMMISSION_RATE_ASC`: Commission rate, lowest first<br>- `COMMISSION_RATE_DESC`: Commission rate, highest first<br>- `PRICE_ASC`: Price, lowest first<br>- `PRICE_DESC`: Price, highest first |
| keyword | string | Search keyword. Supports product ID prefix and title searches. |
| cursor | string | Pagination cursor |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "keyword": "xxxxxx",
    "count": 20,
    "cursor": ""
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| list | []object | List of products |
| list.id | string | Product ID |
| list.cover_id | string | Cover ID |
| list.cover | string | Cover URL |
| list.name | string | Name |
| list.min_price | float64 | Minimum price |
| list.max_price | float64 | Maximum price |
| list.currency | string | Currency type |
| list.commission_rate | number | Commission rate in hundredths of a percentage point. For example, 3587 means 35.87%. Range: `[100, 8000]`. |
| list.is_hidden | bool | Whether the product is hidden |
| list.status | string | Product status. Allowed values:<br>- `ACTIVE`: Available for sale and display<br>- `OUT_OF_STOCK`: Out of stock<br>- `REVIEWING`: New product under initial review and unavailable for sale<br>- `EDITING_REVIEWING`: Changes to an existing product are under review. The product remains available for sale and displays its previous details.<br>- `RESTRICTED`: Platform restriction. Unavailable for sale. |
| cursor | string | Pagination cursor |
| has_more | bool | Whether more results are available |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "cursor": "",
        "has_more": false,
        "after": "",
        "list": [
            {
                "is_hidden": false,
                "status": "ACTIVE",
                "commission_rate": 8000,
                "id": "xxxxxx",
                "cover_id": "xxxxxx",
                "cover": "https://xxxxxx",
                "name": "xxxxxx",
                "min_price": 5.99,
                "max_price": 5.99,
                "currency": "USD"
            }
        ]
    }
}
```
