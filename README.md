<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8E2DE2,100:4A00E0&height=160&section=header" alt="header banner" />

<h1 align="center">Hi there, I'm Arda 👋</h1>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=1000&color=8E2DE2&center=true&vCenter=true&width=600&lines=Backend+%26+Full-Stack+Developer;Spring+Boot+%7C+Kafka+%7C+Python;Open-source+tooling+for+T%C3%BCrkiye" alt="typing intro" />
</p>

<p align="center">
  Computer programming student and full-stack developer. I build backend services, automation that
  runs at real customers, and small open-source tools for software made in Türkiye.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot" />
  <img src="https://img.shields.io/badge/Apache%20Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white" alt="Kafka" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/C%23-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt="C#" />
  <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=for-the-badge&logo=playwright&logoColor=white" alt="Playwright" />
</p>

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

| Package | What it does |
| --- | --- |
| **[trkit](https://github.com/ardazeybek-dev/trkit)** | Correct Turkish casing (`i` → `İ`), TCKN, IBAN and plate validation · `pip install trkit` |
| **[kvkk](https://github.com/ardazeybek-dev/kvkk)** | Finds and masks Turkish personal data in files, logs and dumps · `pip install kvkk` |
| **[bordro](https://github.com/ardazeybek-dev/bordro)** | Turkish payroll: gross ↔ net with cumulative income tax · TypeScript |

## 🧩 Apps

| App | What it does |
| --- | --- |
| **[aktar](https://github.com/ardazeybek-dev/aktar)** | Reads a bank statement, matches payments to people, fills the web panel · in use at a customer |
| **[chatterfix](https://github.com/ardazeybek-dev/chatterfix)** | Windows tray app that fixes the phantom double click of a worn mouse · C# / .NET |

## 🎨 In the Browser

**[K.I.T.T.](https://github.com/ardazeybek-dev/K.I.T.T)** — Knight Rider cockpit with an LLaMA-3 brain, one HTML file · [live demo](https://kitt-arda.shipstatic.com)

More projects on my [repositories page](https://github.com/ardazeybek-dev?tab=repositories).

---

<p align="center">
  <a href="mailto:ardazybk18@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email" /></a>
  <a href="https://www.linkedin.com/in/seyid-arda-zeybek-01a6b43aa"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin" /></a>
</p>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:4A00E0,100:8E2DE2&height=120&section=footer" alt="footer banner" />
