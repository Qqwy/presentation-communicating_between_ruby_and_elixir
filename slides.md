
### Groningen.rb & Elixir |> Groningen

Welcome!

Wifi:<!-- .element: class="tiny-text" --> 
- SSID: Panache,<!-- .element: class="tiny-text" --> 
- password: Elixir|>Groningen<!-- .element: class="tiny-text" -->

---

Agenda

1. Announcement of Code BEAM Lite Amsterdam
2. Talk by **Marten**:
   communicating Ruby <-> Elixir: A multilanguage webapp
3. Talk by **Marcel**: TBA
4. Drinks!

---

## Announcements


---


![](wm_portrait_cutout_ascii_big.png)

Marten (Wiebe-Marten Wijnja)

---

## Communicating between Ruby <-> Elixir: Building a multi-language app

---

### Planga: Seamless Chat Service

---

### Why multiple languages/systems?

| Name                | Chat-service                     | Dashboard-service                           |
|---------------------|----------------------------------|---------------------------------------------|
| Different end-users | Visitors that chat               | Developers that maintain their chat         |
| Concurrent users    | Thousands, Millions              | Hundreds, never more than a couple thousand |
| Downtime            | Immediate problem                | 🤷                                          |
| Interaction         | Instant push-pull; fast          | REST/CRUD                                   |

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

### Communicating:

- Chat-service needs to know what API keys are enabled.
- Dashboard-service needs to know statistics.

TODO insert diagram here

---

### The Past: REST calls to synchronize

Simple to set up, but:

- Security! roll-your-own-encryption?!
- Pull-based, so CRON?
  - fetch everything all the time?
  - Stale info

---

### The Present: RabbitMQ

- Push-based: changes get forwarded.

TODO show some code here

---

### The Joy of working with RabbitMQ :-)

- Great documentation and tutorials!
- Many different configurations of queues

---

### The less joyful parts...

- Security: Setting up TLS is a _must_ for production systems, but a bit of a hassle.
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

### The Future: ???

- Multiple Elixir chat-nodes
  - Distributed datastore (Riak or Cassandra)
  - Potential for less communication, since analytics can be taken directly from distributed datastore.
  - Webhooks, external services to digest/transform messages.


---

### Questions?

---

### Drinks!
Wifi:<!-- .element: class="tiny-text" --> 
- SSID: Panache,<!-- .element: class="tiny-text" --> 
- password: Elixir|>Groningen<!-- .element: class="tiny-text" -->
