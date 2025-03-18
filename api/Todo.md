---
title: Todo
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.29"

---

# Todo

Base URLs:

# Authentication

# Default

## GET List all todos

GET /todos

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|status|query|string| 否 |none|
|page|query|integer| 否 |none|
|limit|query|integer| 否 |none|

#### 枚举值

|属性|值|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

> 返回示例

> 200 Response

```json
{
  "data": [
    {
      "id": "550e8400-e29b-41d4-a716-446655440000",
      "title": "Complete project report",
      "description": "Finalize sections 3-5",
      "status": "pending",
      "dueDate": "2024-03-01T15:00:00Z",
      "categoryId": "337f5e5d-288b-40d5-be14-901cc3acacc0",
      "tagIds": [
        "497f6eca-6276-4993-bfeb-53cbbbba6f08"
      ],
      "memoId": "e4f0bc8d-bb59-4335-ae7a-0c550e3c0edf"
    }
  ],
  "pagination": {
    "total": 0,
    "page": 0,
    "limit": 0
  }
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|A paginated list of todos|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» data|[[Todo](#schematodo)]|false|none||none|
|»» id|string(uuid)|false|none||none|
|»» title|string|true|none||none|
|»» description|string|false|none||none|
|»» status|string|true|none||none|
|»» dueDate|string(date-time)|false|none||none|
|»» categoryId|string(uuid)|false|none||none|
|»» tagIds|[string]|false|none||none|
|»» memoId|string(uuid)|false|none||none|
|» pagination|object|false|none||none|
|»» total|integer|false|none||none|
|»» page|integer|false|none||none|
|»» limit|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

## POST Create a new todo

POST /todos

> Body 请求参数

```json
""
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» title|body|string| 是 |none|
|» description|body|string| 否 |none|
|» categoryId|body|string(uuid)| 否 |none|
|» tagIds|body|[string]| 否 |none|

> 返回示例

> 201 Response

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Complete project report",
  "description": "Finalize sections 3-5",
  "status": "pending",
  "dueDate": "2024-03-01T15:00:00Z",
  "categoryId": "337f5e5d-288b-40d5-be14-901cc3acacc0",
  "tagIds": [
    "497f6eca-6276-4993-bfeb-53cbbbba6f08"
  ],
  "memoId": "e4f0bc8d-bb59-4335-ae7a-0c550e3c0edf"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Todo created|[Todo](#schematodo)|

## GET Get a todo by ID

GET /todos/{todoId}

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|todoId|path|string| 是 |none|

> 返回示例

> 200 Response

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Complete project report",
  "description": "Finalize sections 3-5",
  "status": "pending",
  "dueDate": "2024-03-01T15:00:00Z",
  "categoryId": "337f5e5d-288b-40d5-be14-901cc3acacc0",
  "tagIds": [
    "497f6eca-6276-4993-bfeb-53cbbbba6f08"
  ],
  "memoId": "e4f0bc8d-bb59-4335-ae7a-0c550e3c0edf"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|[Todo](#schematodo)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|none|None|

## PUT Update a todo

PUT /todos/{todoId}

> Body 请求参数

```json
""
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|todoId|path|string| 是 |none|
|body|body|[Todo](#schematodo)| 否 |none|

> 返回示例

> 200 Response

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Complete project report",
  "description": "Finalize sections 3-5",
  "status": "pending",
  "dueDate": "2024-03-01T15:00:00Z",
  "categoryId": "337f5e5d-288b-40d5-be14-901cc3acacc0",
  "tagIds": [
    "497f6eca-6276-4993-bfeb-53cbbbba6f08"
  ],
  "memoId": "e4f0bc8d-bb59-4335-ae7a-0c550e3c0edf"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|[Todo](#schematodo)|

## DELETE Delete a todo

DELETE /todos/{todoId}

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|todoId|path|string| 是 |none|

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Successfully deleted|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|none|None|

## GET Get reminders for a todo

GET /todos/{todoId}/reminders

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|todoId|path|string| 是 |none|

> 返回示例

> 200 Response

```json
[
  {
    "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
    "todoId": "fb0065c9-174d-4e81-9e11-c1b4f674d051",
    "time": "2024-02-28T09:00:00Z",
    "notifyMethod": "email"
  }
]
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|[[Reminder](#schemareminder)]|false|none||none|
|» id|string(uuid)|false|none||none|
|» todoId|string(uuid)|false|none||none|
|» time|string(date-time)|true|none||none|
|» notifyMethod|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|notifyMethod|email|
|notifyMethod|push|
|notifyMethod|sms|

## POST Create a reminder

POST /todos/{todoId}/reminders

> Body 请求参数

```json
""
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|todoId|path|string| 是 |none|
|body|body|[Reminder](#schemareminder)| 否 |none|

> 返回示例

> 201 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "todoId": "fb0065c9-174d-4e81-9e11-c1b4f674d051",
  "time": "2024-02-28T09:00:00Z",
  "notifyMethod": "email"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|[Reminder](#schemareminder)|

## GET List all categories

GET /categories

> 返回示例

> 200 Response

```json
[
  {
    "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
    "name": "Work",
    "color": "#FF5733"
  }
]
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|[[Category](#schemacategory)]|false|none||none|
|» id|string(uuid)|false|none||none|
|» name|string|true|none||none|
|» color|string|false|none||none|

## POST Create a new category

POST /categories

> Body 请求参数

```json
""
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|[Category](#schemacategory)| 否 |none|

> 返回示例

> 201 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "name": "Work",
  "color": "#FF5733"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|[Category](#schemacategory)|

## GET List all tags

GET /tags

> 返回示例

> 200 Response

```json
[
  {
    "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
    "name": "urgent"
  }
]
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|[[Tag](#schematag)]|false|none||none|
|» id|string(uuid)|false|none||none|
|» name|string|true|none||none|

## POST Create a new tag

POST /tags

> Body 请求参数

```json
""
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|[Tag](#schematag)| 否 |none|

> 返回示例

> 201 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "name": "urgent"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|none|[Tag](#schematag)|

## GET Get a memo

GET /memos/{memoId}

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|memoId|path|string| 是 |none|

> 返回示例

> 200 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "content": "Need to discuss with team before submission",
  "attachments": [
    "https://example.com/file.pdf"
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|[Memo](#schemamemo)|

## PUT Update a memo

PUT /memos/{memoId}

> Body 请求参数

```json
""
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|memoId|path|string| 是 |none|
|body|body|[Memo](#schemamemo)| 否 |none|

> 返回示例

> 200 Response

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "content": "Need to discuss with team before submission",
  "attachments": [
    "https://example.com/file.pdf"
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|[Memo](#schemamemo)|

# 数据模型

<h2 id="tocS_Error">Error</h2>

<a id="schemaerror"></a>
<a id="schema_Error"></a>
<a id="tocSerror"></a>
<a id="tocserror"></a>

```json
{
  "error": {
    "code": "NOT_FOUND",
    "message": "Resource not found",
    "details": {}
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|error|object|false|none||none|
|» code|string|false|none||none|
|» message|string|false|none||none|
|» details|object|false|none||none|

<h2 id="tocS_Todo">Todo</h2>

<a id="schematodo"></a>
<a id="schema_Todo"></a>
<a id="tocStodo"></a>
<a id="tocstodo"></a>

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Complete project report",
  "description": "Finalize sections 3-5",
  "status": "pending",
  "dueDate": "2024-03-01T15:00:00Z",
  "categoryId": "337f5e5d-288b-40d5-be14-901cc3acacc0",
  "tagIds": [
    "497f6eca-6276-4993-bfeb-53cbbbba6f08"
  ],
  "memoId": "e4f0bc8d-bb59-4335-ae7a-0c550e3c0edf"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|id|string(uuid)|false|none||none|
|title|string|true|none||none|
|description|string|false|none||none|
|status|string|true|none||none|
|dueDate|string(date-time)|false|none||none|
|categoryId|string(uuid)|false|none||none|
|tagIds|[string]|false|none||none|
|memoId|string(uuid)|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|status|pending|
|status|in_progress|
|status|completed|

<h2 id="tocS_Reminder">Reminder</h2>

<a id="schemareminder"></a>
<a id="schema_Reminder"></a>
<a id="tocSreminder"></a>
<a id="tocsreminder"></a>

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "todoId": "fb0065c9-174d-4e81-9e11-c1b4f674d051",
  "time": "2024-02-28T09:00:00Z",
  "notifyMethod": "email"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|id|string(uuid)|false|none||none|
|todoId|string(uuid)|false|none||none|
|time|string(date-time)|true|none||none|
|notifyMethod|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|notifyMethod|email|
|notifyMethod|push|
|notifyMethod|sms|

<h2 id="tocS_Category">Category</h2>

<a id="schemacategory"></a>
<a id="schema_Category"></a>
<a id="tocScategory"></a>
<a id="tocscategory"></a>

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "name": "Work",
  "color": "#FF5733"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|id|string(uuid)|false|none||none|
|name|string|true|none||none|
|color|string|false|none||none|

<h2 id="tocS_Tag">Tag</h2>

<a id="schematag"></a>
<a id="schema_Tag"></a>
<a id="tocStag"></a>
<a id="tocstag"></a>

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "name": "urgent"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|id|string(uuid)|false|none||none|
|name|string|true|none||none|

<h2 id="tocS_Memo">Memo</h2>

<a id="schemamemo"></a>
<a id="schema_Memo"></a>
<a id="tocSmemo"></a>
<a id="tocsmemo"></a>

```json
{
  "id": "497f6eca-6276-4993-bfeb-53cbbbba6f08",
  "content": "Need to discuss with team before submission",
  "attachments": [
    "https://example.com/file.pdf"
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|id|string(uuid)|false|none||none|
|content|string|false|none||none|
|attachments|[string]|false|none||none|

