
### Groningen.rb & Elixir |> Groningen

Welcome!

Wifi:<!-- .element: class="tiny-text" --> 
- SSID: Panache,<!-- .element: class="tiny-text" --> 
- password: Elixir|>Groningen<!-- .element: class="tiny-text" -->

---

Agenda

1. Announcements
2. Talk by **Marten**:
   communicating Ruby ↔ Elixir: A multilanguage webapp
3. Talk by **Marcel**: Managing side-effects with Phoenix.PubSub
4. Drinks!

---


![](wm_portrait_cutout_ascii_big.png)

Marten (Wiebe-Marten Wijnja)

---

## Announcements

- Code BEAM Amsterdam
- Advent of Code


---

## Communicating between Ruby ↔ Elixir: Building a multi-language app


---

### Planga: Seamless Chat Service

TODO Planga logo

---

- _Existing_ users of your system (no external accounts)
- Chatting _between_ users
- Easy to set up, no extra bandwidth or complexity for your server.

---

Two applications:

- Chat Service
- Dashboard Service

---

### Chat Service:

- Connection handling of visitors
- Persisting and forwarding of messages

---

### Dashboard Service

- Account mamangement
  - Creating new API keys
  - Disabling old API keys
  - Enabling webhooks, etc.
- Analytics

---


### Why multiple languages/systems?

| Name                | Chat-service        | Dashboard-service                           |
|---------------------|---------------------|---------------------------------------------|
| Different end-users | Visitors that chat  | Developers that maintain their chat         |
| Concurrent users    | Thousands, Millions | Hundreds, never more than a couple thousand |
| Downtime            | Immediate problem   | 🤷                                          |
| Interaction         | Instant             | Multiple page loads is fine                 |

- Also: self-hosted Open-Source variant!

---

#### Elixir for chat-application

- Scalability
- Websockets/Phoenix Channels
- Hot-upgrades
- Fault-Tolerance

---

#### Ruby for dashboard-application

- KISS
- Replacability
- Rails is very good at building REST CRUD systems

---

### Communicating:

- Chat-service needs to know what API keys are enabled.
- Dashboard-service needs to know statistics.

TODO insert diagram here

---

### The Past: REST calls

Simple to set up, but:

- Security! roll-your-own-encryption?!
- Pull-based, so CRON?
  - fetch everything all the time?
  - Stale info


---

### The Present: Persistent Messaging

#### RabbitMQ

- Push-based: changes get forwarded.
- Nice: 
  - Great documentation and tutorials!
  - Many different configurations of queues
- Less nice:
  - Not so clear on how to configure for production
  

---

### Aside: Security

- Setting up TLS with peer-verification is a _must_ for production systems; difficult to set up.
- XCA: GUI to make certificates.
- Terminating proxies (Nginx) to the rescue!

---

### Erlang External Term Format (ETF)

- Better fit than JSON, because:
  - 1:1 mapping of many datatypes between Ruby and Elixir:
     - Symbols/Atoms
     - BigNums
  - Compressed
  - No weird restrictions on top-level types
  - Elixir is 'host' system so it should dictate typing.

---

TODO Code examples:

- Ruby producer
- Call sites in Ruby code (after creation/update, at startup)

- Elixir consumer
- TODO Elixir producer at startup

---

### The Future: ???

- Multiple Elixir chat-nodes
  - Distributed datastore (Riak or Cassandra)
  - Potential for less communication, since analytics can be taken directly from distributed datastore.
  
TODO graphic of long-term app architecture


---

### Questions?

---

### Drinks!
Wifi:<!-- .element: class="tiny-text" --> 
- SSID: Panache,<!-- .element: class="tiny-text" --> 
- password: Elixir|>Groningen<!-- .element: class="tiny-text" -->
