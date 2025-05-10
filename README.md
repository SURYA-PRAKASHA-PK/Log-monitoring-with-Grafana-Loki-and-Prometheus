# Log Monitoring and Observability Platform with Loki, Prometheus, and Grafana

## Overview
This project implements a unified log monitoring and observability platform using **Loki**, **Prometheus**, and **Grafana**—all orchestrated via Docker Compose. The system demonstrates how to collect, store, and visualize both logs and metrics, providing powerful insights for monitoring and troubleshooting modern applications.

---

## The Big Picture
This setup creates a robust observability platform where log data and metrics data are collected, stored, and visualized in a unified dashboard. The key insight is that logs and metrics complement each other:
- **Metrics** show you trends and patterns at scale
- **Logs** provide detailed context for troubleshooting

By correlating metrics and logs from the same source, you can quickly identify, investigate, and resolve issues.

---

## Architecture & Components
The system consists of the following main components:

- **Log Generator**: Simulates application activity by generating sample JSON logs.
- **Promtail**: Loki's agent that collects and ships logs to Loki.
- **Loki**: Stores and indexes logs for fast querying.
- **Metrics Exporter**: Extracts metrics from logs and exposes them for Prometheus.
- **Prometheus**: Collects and stores time-series metrics.
- **Grafana**: Visualizes both logs and metrics in unified dashboards.

All components are defined and orchestrated in a single `docker-compose.yaml` file for easy deployment.

---

## Running the Stack
1. **Clone the repository**
2. **Start all services:**
   ```sh
   docker-compose up -d
   ```

3. **Access the services:**
   - **Grafana:** [http://localhost:3000](http://localhost:3000)
   - **Prometheus:** [http://localhost:9090](http://localhost:9090)
   - **Loki:** via Grafana (already configured as a data source)

---

## Building and Using the Dashboard

### Importing the Dashboard
- In Grafana, go to **Dashboards > Import**
- Upload the provided `grafana-dashboard.json` file
- Select your Prometheus and Loki data sources when prompted

### Example Dashboards
Below are example screenshots from the Grafana dashboard, demonstrating the power of unified log and metric visualization:

#### High-Level Overview
![Dashboard Overview 1](https://github.com/SURYA-PRAKASHA-PK/Log-monitoring-with-Grafana-Loki-and-Prometheus/blob/master/dashboard-overview-1.png.png)

#### Detailed Metrics and Log Correlation
![Dashboard Overview 2](https://github.com/SURYA-PRAKASHA-PK/Log-monitoring-with-Grafana-Loki-and-Prometheus/blob/master/dashboard-overview-2.png.png)

---

## Dashboard Features
- **Request Rate by Method**: Visualizes HTTP request rates by method using Prometheus metrics.
- **Raw Logs Panel**: Displays actual log entries from Loki, filtered by method or status code.
- **Status Code Distribution**: Shows error rates and response patterns over time.
- **Response Time and Size**: Monitors performance and payload sizes.
- **Top 10 Slowest Endpoints**: Identifies performance bottlenecks.
- **Interactive Filtering**: Use template variables to filter by service, HTTP method, or status code—keeping all panels in sync.

---

## The Power of Correlation
- **Observe**: Spot spikes or anomalies in metrics panels
- **Investigate**: Instantly filter logs to the same time and context
- **Diagnose**: Read detailed log entries to find root causes

This direct correlation between high-level metrics and detailed logs is the core strength of the solution.

---

## Extending the System
- Replace the log generator with your real application logs
- Expand metrics extraction to cover more business or technical KPIs
- Scale out components for production workloads

---

## Conclusion
This project is more than just a monitoring solution—it's a unified observability platform that combines the strengths of metrics and logs:
- **Metrics** provide the big picture, helping identify when and where problems occur
- **Logs** provide the details, helping determine why those problems occurred

By combining Loki, Prometheus, and Grafana in a Docker-based setup, you gain a powerful tool for both monitoring system health and troubleshooting issues as they arise.

---

## Repository Structure
- `docker-compose.yaml` — All-in-one stack definition
- `grafana-dashboard.json` — Prebuilt Grafana dashboard
- `config/` — Configuration files for Loki, Promtail, Prometheus, etc.
- `scripts/` — Log generator and metrics exporter scripts
- `images/` — Dashboard screenshots for documentation

---

## License
This project is open source and available under the MIT License.
