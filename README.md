<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:8E2DE2,100:4A00E0&height=160&section=header" alt="header banner" />

<h1 align="center">Hi there, I'm Arda 👋</h1>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=1000&color=8E2DE2&center=true&vCenter=true&width=600&lines=Full-Stack+Developer;Frontend+Developer;Backend+Developer;Desktop+App+Developer;Automation+%26+Open-Source+Tools" alt="typing intro" />
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
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" />
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
  <img src="https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt=".NET" />
  <img src="https://img.shields.io/badge/Tailwind-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind" />
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="Redis" />
  <img src="https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white" alt="RabbitMQ" />
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions" />
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

## 🐍 Watch the Snake Eat My Contributions

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ardazeybek-dev/ardazeybek-dev/output/github-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ardazeybek-dev/ardazeybek-dev/output/github-snake.svg" />
    <img alt="github contribution snake animation" src="https://raw.githubusercontent.com/ardazeybek-dev/ardazeybek-dev/output/github-snake.svg" width="100%" />
  </picture>
</p>

---

<p align="center">
  <img width="85%" src="assets/quotes.svg" alt="rotating programming quotes" />
</p>

---

<p align="center">
  <a href="https://mail.google.com/mail/?view=cm&fs=1&to=ardazybk18@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email" /></a>
  <a href="https://www.linkedin.com/in/seyid-arda-zeybek-01a6b43aa"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin" /></a>
  <a href="https://pypi.org/user/ardazeybek-dev/"><img src="https://img.shields.io/badge/PyPI-3775A9?style=for-the-badge&logo=pypi&logoColor=white" alt="pypi" /></a>
  <a href="https://www.npmjs.com/~ardazeybek-dev"><img src="https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white" alt="npm" /></a>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=18&duration=2500&pause=800&color=39D353&center=true&vCenter=true&width=520&lines=Thanks+for+visiting!+%F0%9F%91%8B;Keep+building+cool+things+%F0%9F%9A%80;Complexity+is+easy%3B+simplicity+takes+courage" alt="footer typing animation" />
</p>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:4A00E0,100:8E2DE2&height=120&section=footer" alt="footer banner" />
