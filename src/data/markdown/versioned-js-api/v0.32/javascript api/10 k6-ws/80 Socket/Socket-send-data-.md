---
title: 'Socket.send(data)'
excerpt: 'Send a data string through the connection.'
---

Send a data string through the connection.
You can use `JSON.stringify` to convert a JSON or JavaScript values to a JSON string.

| Parameter | Type   | Description       |
| --------- | ------ | ----------------- |
| data      | string | The data to send. |

### Example

<CodeGroup labels={[]}>

```javascript
import ws from 'k6/ws';

export default function () {
  var url = 'ws://echo.websocket.org';
  var response = ws.connect(url, null, function (socket) {
    socket.on('open', function () {
      socket.send('my-message');
      socket.send(JSON.stringify({ data: 'hola' }));
    });
  });
}
```

</CodeGroup>

- See also [Socket.sendBinary(data)](/v0.32/javascript-api/k6-ws/socket/socket-sendbinary-data)