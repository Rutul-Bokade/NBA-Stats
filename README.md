# NBA Analytics Platform 🏀



---

![NBA Workflow](https://github.com/nogibjj/BallersDash/assets/141798228/0d6e250c-9c80-4ed6-ab75-fc1b20d87adc)

BallersDash is a comprehensive NBA analytics platform tailored for basketball enthusiasts, fantasy team managers, and sports bettors. With live updates and a fully interactive design, this Streamlit-based dashboard delivers insights through advanced data visualizations, head-to-head matchups, raw team stats, and probability-driven forecasts.

---

## 📊 Data Backbone

**Primary Source: Basketball Reference**

Our data pipeline pulls rich NBA datasets including:

* Player and team stats (points, assists, FG%, etc.)
* Game-by-game logs
* Advanced analytics and comparisons
* Trades, historical data, and injury updates

---

## 🔍 Key Features

### 1. Matchup Intelligence

Break down matchups with win/loss histories, point spreads, and interactive CDF-based point spread forecasts.

### 2. Deep Stats Dive

Track raw stats for any NBA team across specific game spans (last 5/10/15/all). View trends, strengths, and outliers.

### 3. Live Visual Exploration

Dynamic filters let users explore data across teams, timeframes, and stat categories—delivered through interactive graphs.

### 4. Power Rankings

Teams are evaluated with a custom algorithm that ranks relative strength—adjusted for context.

### 5. Point Spread Analytics

Explore PDF and CDF graphs visualizing likely point differentials based on recent performance.

### 6. Game Differential Plotting

View an evolving visual of head-to-head point differences—highlighting seasonal momentum.

### 7. Injury Watch

Always stay updated with a real-time injury table that informs team performance analysis.

### 8. Stat Visuals (Dynamic Graphs)

Visualize win percentages, shooting stats, defensive rebounds, and more—fully customizable per user input.

---

## 💻 Platform UI

![dashboard\_display](https://github.com/nogibjj/BallersDash/assets/141798228/7218eea3-0fd0-4939-9d6a-efc9f8d4a394)

The user-friendly Streamlit interface allows:

* Date-based filtering
* Team/game selections
* Intuitive navigation between analytics and visuals

---

## ⚙️ End-to-End ETL Workflow

### 🔄 1. Data Pull

Raw team-level data is extracted daily from Basketball Reference.

### 🧠 2. Spark-Based Transformation

Apache Spark handles transformations and aggregates via DataFrames for performance and scalability.

### 🏢 3. Data Loading

Transformed outputs are pushed to Azure Databricks SQL Warehouse.

### ⏰ 4. Scheduler

Pipeline auto-runs every day at 6 AM to keep the dashboard updated.

### 🐍 5. Python Logic Layer

A Python orchestrator manages extraction, transformation, and analytics from within a Databricks cluster.

### 🌐 6. Web Interface

The frontend (Streamlit) fetches, processes, and displays data via user-defined filters and visualization modules.

---

## 📈 Visualizations

### PDF Graph

![pdf](https://github.com/nogibjj/BallersDash/assets/36940292/bdc3f5e7-f7d4-40a9-bc9d-cf730c88dcc0)

### CDF Graph

![CDF](https://github.com/nogibjj/BallersDash/assets/36940292/eed857f6-5bb9-469a-a22b-78e161f54a23)

### Point Difference Table & Plot

![image](https://github.com/nogibjj/BallersDash/assets/36940292/543b38b2-eb84-4211-b991-aed205215ceb)
![scaled\_stats](https://github.com/nogibjj/BallersDash/assets/36940292/a911421c-16ce-4273-b218-0de44bed26af)

### Dynamic Stat Plots

![raw\_stats\_dynamic](https://github.com/nogibjj/BallersDash/assets/36940292/abea8a29-244d-4706-9bab-89099cc10d09)

### Raw Table

![raw\_stats\_head](https://github.com/nogibjj/BallersDash/assets/141798228/77082248-4ed6-4a95-a6e0-1f2051decc9c)

### Injury Feed

![injury\_report](https://github.com/nogibjj/BallersDash/assets/141798228/c59a77d3-c4c5-4086-8e11-b1f5eb50d755)

---

## 📎 Logging System

Our logger monitors pipeline execution from data scraping to processing. Messages include timestamps and severity levels (DEBUG, INFO, ERROR). Logs also capture API calls and status updates for each NBA team processed.

![logging\_screenshot](https://github.com/nogibjj/BallersDash/assets/141798228/40fc0092-603a-44da-a59e-4aed950c82a4)

---

## ☁️ Azure Deployment + Docker

The project is deployed on Azure Web App via Docker, using a containerized microservice image built with Python. Docker simplifies deployment and improves consistency across environments.

* DockerHub: [https://hub.docker.com/repository/docker/shawir/nbastats/general](https://hub.docker.com/repository/docker/shawir/nbastats/general)
* Container image includes streamlined dependencies and logging for better traceability.

![dockerhub\_final](https://github.com/nogibjj/BallersDash/assets/141798228/87f449c9-7535-48fb-86a0-19fcffccc13f)

---

## 🚀 CI/CD with GitHub Actions

The Makefile automates CI/CD tasks:

* Dependency installation
* Linting via `ruff` and Dockerfile validation with `hadolint`
* Black formatting
* Placeholder deployment target for future steps

---

## 🧲 Load Testing via Locust

We used Locust to simulate 10,000 users to test platform scalability. Response time plots from these tests revealed valuable performance bottlenecks.

![total\_requests\_per\_second\_1702180797-2](https://github.com/nogibjj/BallersDash/assets/89782802/aafea4ee-643d-4c25-aa06-f7bbf0a6e73d)

---

## 🛠️ Data Engineering + IaC

* Spark handles all transformation logic
* Data is stored in Azure Databricks SQL Warehouse
* Infrastructure is deployed via Terraform (Infrastructure as Code)
* The daily 6 AM ETL schedule automates analytics delivery

---

## 👨‍💻 AI Dev Tools

### GitHub Copilot

* Helped construct Locust files and Docker image
* Assisted with syntax and logic debugging

### Databricks Assistant

* Helped generate SQL queries
* Suggested transformation logic within Notebooks

---

## 🗜️ Challenges & Next Steps

### Constraints:

* Limited Azure credits constrained deeper experimentation
* Docker images occupied significant local storage

### Future Enhancements:

* Expand UI with more team visuals and stat categories
* Add team-specific historical performance pages

---

## 🛠️ Run It Yourself

```bash
streamlit run mylib/nbastatsdash.py
```

The dashboard will be accessible via localhost. The ETL pipeline will populate your Databricks instance with fresh NBA stats daily at 6 AM.
