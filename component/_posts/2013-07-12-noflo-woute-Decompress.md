---
  title: "Decompress"
  library: "noflo-woute"
  layout: "component"

---

```coffeescript
EXPORT=INPUT.IN:IN
EXPORT=BODY.OUT:OUT
EXPORT=HEADERS.OUT:HEADERS
EXPORT=SESSIONID.OUT:TOKEN
EXPORT=URL.OUT:URL
EXPORT=RESPONSE.OUT:RESPONSE
EXPORT=QUERY.OUT:QUERY

'headers' -> ROUTE Router(routers/GroupRouter)
Input(Repeat) OUT -> IN Router() OUT -> IN Headers(adapters/ObjectToPackets)

'body' -> ROUTE Router()
Router() OUT -> IN Body(adapters/ObjectToPackets)

'session-id' -> ROUTE Router()
Router() OUT -> IN SessionId(Repeat)

'url' -> ROUTE Router()
Router() OUT -> IN Url(Repeat)

'response' -> ROUTE Router()
Router() OUT -> IN Response(Repeat)

'query' -> ROUTE Router()
Router() OUT -> IN Query(Repeat)

```