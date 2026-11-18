# Get BiliBili Category IDs

### Request URL

`https://www.upmee.cc/open_api/media/task/bilibili/type/list`

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

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | string | Team ID |

### Request Example

```json
{
    "team_id": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| id | int | Category ID. `0` denotes the root node. |
| parent | int | Parent category ID |
| name | string | Category name |
| description | string | Category description |
| children | obj | Same structure as the top-level category |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 160,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 211,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 211,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 211,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 211,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 211,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 4,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 3,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 155,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 155,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 155,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 155,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 36,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 5,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 5,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 5,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 5,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 181,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 181,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 181,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 181,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 1,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 223,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 217,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 217,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 217,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 217,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 217,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 217,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 129,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 129,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 129,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 129,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 129,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 129,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 188,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 188,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 188,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 188,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 188,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 234,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 234,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 234,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 234,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 234,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 234,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 167,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 167,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 167,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 167,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 167,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 119,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 119,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 119,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 119,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 119,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 177,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 177,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 177,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 177,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 11,
                        "name": "xxxxxx",
                        "description": ""
                    },
                    {
                        "id": 0,
                        "parent": 11,
                        "name": "xxxxxx",
                        "description": ""
                    }
                ]
            },
            {
                "id": 0,
                "parent": 0,
                "name": "xxxxxx",
                "description": "xxxxxx",
                "children": [
                    {
                        "id": 0,
                        "parent": 13,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 13,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 13,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    },
                    {
                        "id": 0,
                        "parent": 13,
                        "name": "xxxxxx",
                        "description": "xxxxxx"
                    }
                ]
            }
        ]
    }
}
```
