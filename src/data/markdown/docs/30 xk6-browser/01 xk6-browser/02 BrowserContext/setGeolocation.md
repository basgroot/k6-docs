---
title: 'setGeolocation(geolocation)'
excerpt: "Sets the context's geolocation."
---

Sets the context's geolocation.

| Parameter   | Type   | Description                                          |
| ---------   | ------ | ---------------------------------------------------- |
| geolocation | object |                                                      |
| - latitude  | number | Latitude between -90 and 90.                         |
| - longitude | number | Latitude between -180 and 180.                       |
| - accuracy  | number | Optional non-negative accuracy value. Defaults to 0. |


### Example

<!-- eslint-skip -->

<CodeGroup labels={[]}>

```javascript
const context = browser.newContext();
context.setGeolocation({latitude: 59.95, longitude: 30.31667});
```

</CodeGroup>