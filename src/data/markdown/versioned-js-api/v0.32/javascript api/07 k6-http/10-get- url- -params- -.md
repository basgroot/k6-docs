---
title: 'get( url, [params] )'
description: 'Issue an HTTP GET request.'
excerpt: 'Issue an HTTP GET request.'
---

Make a GET request.

| Parameter         | Type   | Description                                                                                     |
| ----------------- | ------ | ----------------------------------------------------------------------------------------------- |
| url               | string | Request URL (e.g. `http://example.com`).                                                        |
| params (optional) | object | [Params](/v0.32/javascript-api/k6-http/params) object containing additional request parameters. |

### Returns

| Type                                               | Description           |
| -------------------------------------------------- | --------------------- |
| [Response](/v0.32/javascript-api/k6-http/response) | HTTP Response object. |

### Example fetching a URL

<CodeGroup labels={[]}>

```javascript
import http from 'k6/http';

export default function () {
  let res = http.get('https://k6.io');
  console.log(JSON.stringify(res.headers));
}
```

</CodeGroup>