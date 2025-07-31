---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Writing WebSocket client applications"
description: "WebSocket(), send(), onmessage(), close()"
date: 2025-06-09
author: "tdtc"
---

[Req](https://caniuse.com/?search=websocket) ：
```
Android Browser: v4.4+
Safari supported: v5/6+
```

- [WebSocket()](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
- [send()](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket/send)
- [onmessage()](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket/message_event)
- [close()](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket/close)

## Creating a WebSocket object
```
webSocket = new WebSocket(url, protocols);
```
- protocols
> Optional

### [URI Schemes](https://www.rfc-editor.org/rfc/rfc6455#section-11.1)
- wss
```
Equivalent to HTTPs.
```
Connection confidentiality and integrity is provided by running the WebSocket Protocol over TLS (wss URIs).

### Connection errors
- [Status Codes](https://datatracker.ietf.org/doc/html/rfc6455#section-7.4.1)
```
1000 ~ 1011,  1015
```

### Examples
```
const exampleSocket = new WebSocket(
  "wss://www.example.com/socketserver"
);
```

## Sending data to the server
```
exampleSocket.send("Here's some text that the server is urgently awaiting!");
```
You can send data as a string, Blob, or ArrayBuffer.

### Using JSON to transmit objects
```
// Send text to all users through the server
function sendText() {
  // Construct a msg object containing the data the server needs to process the message from the chat client.
  const msg = {
    type: "message",
    text: document.getElementById("text").value,
    id: clientID,
    date: Date.now(),
  }

  // Send the msg object as a JSON-formatted string.
  exampleSocket.send(JSON.stringify(msg));

  // Blank the text input element, ready to receive the next line of text from the user.
  document.getElementById("text").value = "";
}
```

## Receiving messages from the server
```
exampleSocket.onmessage = (event) => {
  console.log(event.data);
};
```

### Receiving and interpreting JSON objects
```
exampleSocket.onmessage = (event) => {
  const f = document.getElementById("chat-box").contentDocument;
  let text = "";
  const msg = JSON.parse(event.data);
  const time = new Date(msg.date);
  const timeStr = time.toLocaleTimeString();

  switch (msg.type) {
    case "id":
      clientID = msg.id;
      setUsername();
      break;
    case "username":
      text = `User <em>${msg.name}</em> signed in at ${timeStr}<br>`;
      break;
    case "message":
      text = `(${timeStr}) ${msg.name} : ${msg.text} <br>`;
      break;
    case "reject-username":
      text = `Your username has been set to <em>${msg.name}</em> because the name you chose is in use.<br>`;
      break;
    case "user-list":
      document.getElementById("user-list-box").innerText = msg.users.join("\n");
      break;
  }

  if (text.length) {
    f.write(text);
    document.getElementById("chat-box").contentWindow.scrollByPages(1);
  }
};
```

## Closing the connection
```
exampleSocket.close();
```

## Ref
- [Writing WebSocket client applications](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications)
