# Hi, I'm Arda 👋

Computer programming student and full-stack developer. I build backend services, automation that
runs at real customers, and small open-source tools for software made in Türkiye.

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![C#](https://img.shields.io/badge/C%23-512BD4?style=flat-square&logo=dotnet&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)

---

## ⭐ Featured — [spring-kafka-orders](https://github.com/ardazeybek-dev/spring-kafka-orders)

Two Spring Boot microservices that talk only through Apache Kafka: key-based ordering, parallel
consumers with row locking, retries, a dead letter topic and idempotent consumers — each failure
triggered by hand and covered by a test.

```mermaid
flowchart LR
    client([client])
    subgraph order-service
        api[REST API] --> odb[(orders)]
        srl[stock-results listener] --> odb
    end
    subgraph Kafka
        orders[[orders]]
        results[[stock-results]]
        dlt[[orders.DLT]]
    end
    subgraph inventory-service
        ol[orders listener] --> idb[(products +<br/>processed events)]
    end

    client -->|POST /orders| api
    api -->|OrderCreated<br/>key = orderId| orders
    orders --> ol
    ol -->|StockResult| results
    ol -. failed after retries .-> dlt
    results --> srl
```

<details>
<summary>Order lifecycle</summary>

```mermaid
sequenceDiagram
    participant C as Client
    participant O as order-service
    participant K as Kafka
    participant I as inventory-service
    C->>O: POST /orders
    O->>K: OrderCreated
    O-->>C: 201 PENDING
    K->>I: OrderCreated
    I->>I: check eventId, lock row, reserve stock
    I->>K: StockResult
    K->>O: StockResult
    O->>O: CONFIRMED / REJECTED
```

</details>

---

## 📦 Packages

| | |
| --- | --- |
| **[trkit](https://github.com/ardazeybek-dev/trkit)** | Correct Turkish casing (`i` → `İ`), TCKN, IBAN and plate validation · `pip install trkit` |
| **[kvkk](https://github.com/ardazeybek-dev/kvkk)** | Finds and masks Turkish personal data in files, logs and dumps · `pip install kvkk` |
| **[bordro](https://github.com/ardazeybek-dev/bordro)** | Turkish payroll: gross ↔ net with cumulative income tax · TypeScript |

## 🧩 Apps

| | |
| --- | --- |
| **[aktar](https://github.com/ardazeybek-dev/aktar)** | Reads a bank statement, matches payments to people, fills the web panel · in use at a customer |
| **[chatterfix](https://github.com/ardazeybek-dev/chatterfix)** | Windows tray app that fixes the phantom double click of a worn mouse · C# / .NET |

## 🎨 In the Browser

**[K.I.T.T.](https://github.com/ardazeybek-dev/K.I.T.T)** — Knight Rider cockpit with an LLaMA-3 brain, one HTML file · [live demo](https://kitt-arda.shipstatic.com)

More projects on my [repositories page](https://github.com/ardazeybek-dev?tab=repositories).

---

📫 [ardazybk18@gmail.com](mailto:ardazybk18@gmail.com) · [LinkedIn](https://www.linkedin.com/in/seyid-arda-zeybek-01a6b43aa)
