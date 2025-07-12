# NBA Stats - Real-Time Basketball Analytics Dashboard 🏀

![CI Badge](https://github.com/nogibjj/BallersDash/actions/workflows/cicd.yml/badge.svg)

---

![NBA Workflow](https://github.com/nogibjj/BallersDash/assets/141798228/0d6e250c-9c80-4ed6-ab75-fc1b20d87adc)

**NBA Stats** is a modern, scalable NBA data visualization and prediction tool designed for basketball strategists, fantasy sports players, and analytics enthusiasts. Built using Streamlit and powered by Databricks, it transforms raw statistical data into interactive visual storytelling and forecasts.

---

## 🔗 System Architecture Overview

* **ETL Pipeline:** Daily 6 AM updates from Basketball Reference
* **Spark Processing:** Aggregates and transforms raw data
* **SQL Warehouse:** Hosted on Azure Databricks for scalable querying
* **Front-End:** Streamlit interface with dynamic visualizations
* **Deployment:** Docker + Azure Web App

---

## 📊 Data Ingestion

**Source: Basketball Reference**

We scrape and process the following datasets:

* Player/game logs
* Team splits and metrics
* Injury updates
* Historical season data
* Advanced metrics

---

## 🔬 Key Functional Modules

### 🤝 Match Analytics Engine

* Generates team comparison dashboards
* Calculates win/loss, recent trends, and point spreads
* Includes interactive CDF probability tables

### 📅 Game History Lookup

* Review last 5, 10, 15, or all games
* Raw stats filtered by shooting, defense, and possessions

### 🔄 Dynamic Graph Studio

* Interactive PDF/CDF graphs for match outcomes
* Trend lines for field goal %, rebounds, and more

### 📈 Rankings + Power Index

* Custom algorithm adjusts for strength of schedule
* Team rankings shift in real-time

### 🪑 Injury Dashboard

* Daily refreshed injury tracker
* Supports pre-game decision making

### 🕹️ Visual Panel

* Explore stats, outcomes, and rankings through:

  * Point differential plots
  * Scaled stats graphs
  * Game-by-game plots

---

## 🔢 Visualization Gallery

**PDF (Probability Distribution Function):**
![pdf](https://github.com/nogibjj/BallersDash/assets/36940292/bdc3f5e7-f7d4-40a9-bc9d-cf730c88dcc0)

**CDF (Cumulative Distribution Function):**
![CDF](https://github.com/nogibjj/BallersDash/assets/36940292/eed857f6-5bb9-469a-a22b-78e161f54a23)

**Point Differential Trends:**
![image](https://github.com/nogibjj/BallersDash/assets/36940292/543b38b2-eb84-4211-b991-aed205215ceb)
![scaled\_stats](https://github.com/nogibjj/BallersDash/assets/36940292/a911421c-16ce-4273-b218-0de44bed26af)

**Raw Performance Stats:**
![raw\_stats\_dynamic](https://github.com/nogibjj/BallersDash/assets/36940292/abea8a29-244d-4706-9bab-89099cc10d09)

**Tabular Summary:**
![raw\_stats\_head](https://github.com/nogibjj/BallersDash/assets/141798228/77082248-4ed6-4a95-a6e0-1f2051decc9c)

**Injury Feed:**
![injury\_report](https://github.com/nogibjj/BallersDash/assets/141798228/c59a77d3-c4c5-4086-8e11-b1f5eb50d755)

---

## ✈️ Deployment & Automation

### Docker + Azure:

* Docker image published to [DockerHub](https://hub.docker.com/repository/docker/shawir/nbastats/general)
* Hosted on Azure Web App for external access

### GitHub Actions CI/CD:

* Dependency management
* Linting via `ruff`, `hadolint`, and `black`
* Future-ready deployment hooks

![dockerhub\_final](https://github.com/nogibjj/BallersDash/assets/141798228/87f449c9-7535-48fb-86a0-19fcffccc13f)

---

## 🤬 Load Testing and Diagnostics

**Tool Used:** Locust

* Simulated 10,000 concurrent users
* Captured requests per second and response time bottlenecks

![total\_requests\_per\_second\_1702180797-2](https://github.com/nogibjj/BallersDash/assets/89782802/aafea4ee-643d-4c25-aa06-f7bbf0a6e73d)

---

## 📁 Logging Infrastructure

Tracks:

* Pipeline events (pull, transform, load)
* HTTPS requests
* Errors by team + timestamp

![logging\_screenshot](https://github.com/nogibjj/BallersDash/assets/141798228/40fc0092-603a-44da-a59e-4aed950c82a4)

---

## 🪯 Development Aids

### GitHub Copilot:

* Assisted in Docker build and Locust scripting
* Debugged Python loops and streamlit components

### Databricks Assistant:

* Suggested SQL queries and join logic
* Generated metadata-aware ETL snippets

---

## 🧪 Engineering Stack

| Layer         | Technology                        |
| ------------- | --------------------------------- |
| ETL           | Python + Spark                    |
| DB            | Azure SQL Warehouse               |
| Infra         | Terraform IaC + Azure App Service |
| Viz           | Streamlit                         |
| Orchestration | GitHub Actions + Cron             |

---

## ⚒️ Challenges & Optimizations

**Constraints:**

* Limited Azure budget = reduced VM usage
* Docker layers caused local storage issues

**Enhancements Planned:**

* Enhanced Streamlit UX with images + animation
* Add user-specific saved views + stat tracking

---

## ▶️ Run the App Locally

```bash
streamlit run mylib/nbastatsdash.py
```

App will launch at `localhost:8501`.

ETL updates NBA stats each morning via a 6 AM cron job running in Azure Databricks.
