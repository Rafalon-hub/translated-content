---
title: EventSource
slug: Web/API/EventSource
tags:
  - API
  - Communications
  - EventSource
  - Interface
  - NeedsTranslation
  - Reference
  - Server Sent Events
  - Server-sent events
  - TopicStub
  - messaging
translation_of: Web/API/EventSource
---
{{APIRef("Server Sent Events")}}

**`EventSource`** 인터페이스는 [server-sent events](/ko/docs/Web/API/Server-sent_events)에 대한 웹 콘텐츠 인터페이스입니다. `EventSource` 인스턴스는 `text/event-stream` 포맷으로 이벤트를 보내는 [HTTP](/ko/docs/Web/HTTP) 서버에 지속적인 연결을 합니다. 연결은{{domxref("EventSource.close()")}} 호출로 종료되지 전까지 지속됩니다.

연결이 시작되었을 때, 서버로부터 들어오는 메세지들은 이벤트의 형태로 코드에 전달됩니다. 들어온 메시지에 이벤트 필드가 있다면, 트리거된 이벤트는 이벤트 필드의 값과 같게 됩니다. 만약 이벤트 필드가 비어있다면, 그 땐 제네릭 {{event("message")}} 이벤트가 발생됩니다.

[웹소켓](/ko/docs/Web/API/WebSockets_API)과 다르게, server-sent 이벤트는 단방향입니다. 데이터 메시지가 서버에서 클라이언트로 (유저의 웹 브라우저 같은) 한 방향으로 전달되는 것입니다. 이 특징은 클라이언트에서 서버로 메시지 형태로 데이터를 보낼 필요가 없을 때, server-sent 이벤트를 훌륭한 선택으로 만든다. 예를 들어, `EventSource` 는 소셜 미디어 상태 업데이트, 뉴스피드나 [IndexedDB](/ko/docs/Web/API/IndexedDB_API)나 [web storage](/ko/docs/Web/API/Web_Storage_API)같은 [클라이언트-사이드 저장](/ko/docs/Learn/JavaScript/Client-side_web_APIs/Client-side_storage) 매커니즘으로 데이터를 전달하는 데 유용한 접근법입니다.

## Constructor

- {{domxref("EventSource.EventSource", "EventSource()")}}
  - : Creates a new `EventSource` to handle receiving server-sent events from a specified URL, optionally in credentials mode.

## Properties

_This interface also inherits properties from its parent, {{domxref("EventTarget")}}._

- {{domxref("EventSource.readyState")}} {{readonlyinline}}
  - : A number representing the state of the connection. Possible values are `CONNECTING` (`0`), `OPEN` (`1`), or `CLOSED` (`2`).
- {{domxref("EventSource.url")}} {{readonlyinline}}
  - : A {{domxref("DOMString")}} representing the URL of the source.
- {{domxref("EventSource.withCredentials")}} {{readonlyinline}}
  - : A {{domxref("Boolean")}} indicating whether the `EventSource` object was instantiated with cross-origin ([CORS](/ko/docs/Web/HTTP/CORS)) credentials set (`true`), or not (`false`, the default).

### Event handlers

- {{domxref("EventSource.onerror")}}
  - : Is an {{event("Event_handlers", "event handler")}} called when an error occurs and the {{event("error")}} event is dispatched on an `EventSource` object.
- {{domxref("EventSource.onmessage")}}
  - : Is an {{event("Event_handlers", "event handler")}} called when a {{event("message")}} event is received, that is when a message is coming from the source.
- {{domxref("EventSource.onopen")}}
  - : Is an {{event("Event_handlers", "event handler")}} called when an {{event("open")}} event is received, that is when the connection was just opened.

## Methods

이 인터페이스는 부모인 *{{domxref("EventTarget")}}*으로부터 메소드를 상속받고 있습니다.

- {{domxref("EventSource.close()")}}
  - : Closes the connection, if any, and sets the `readyState` attribute to `CLOSED`. If the connection is already closed, the method does nothing.

## 예시

이 기초적인 예시에서, `EventSource`는 서버로 부터 받은 이벤트로 생성되었습니다; `"sse.php"`라는 이름을 가진 페이지는 이벤트를 생성할 책임이 있습니다.

```js
var evtSource = new EventSource('sse.php');
var eventList = document.querySelector('ul');

evtSource.onmessage = function(e) {
  var newElement = document.createElement("li");

  newElement.textContent = "message: " + e.data;
  eventList.appendChild(newElement);
}
```

각각의 수신한 이벤트는 우리의 `EventSource` 객체의 `onmessage` 이벤트 핸들러가 실행되도록 합니다. 차례가 되었을 때, 새로운 {{HTMLElement("li")}} 요소를 생성하고, 메시지 데이터를 안에 작성합니다. 그 때, 문서에 이미 존재하는 ul 요소에 새로운 요소를 추가하게 됩니다.

> **참고:** You can find a full example on GitHub — see [Simple SSE demo using PHP.](https://github.com/mdn/dom-examples/tree/master/server-sent-events)

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Server-sent events](/ko/docs/Web/API/Server-sent_events)
- [Using server-sent events](/ko/docs/Web/API/Server-sent_events/Using_server-sent_events "en/Server-sent events/Using server-sent events")
