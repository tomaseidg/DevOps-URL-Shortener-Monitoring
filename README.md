# DevOps-URL-Shortener-Monitoring-Project

Monitoring a Containerized URL Shortener Webservice under the supervision of Digital Egypt Pioneers Initiative

![Project Banner](https://drive.google.com/uc?export=view&id=1avVWO62IfilW49j8yMclbMgdOHLlrJ0K)

---

## Team members
- Thomas Eid Gerges Sureal.
- Moaaz Zaki Ismail Zaki.
- Nourhan Khalid Ahmed Mahmoud.
- Sherif Mostafa Abdelaziz Mohamed.
- Mariam Ahmed Soude ElSayed.

---

## Project Overview
This project involves creating a webservice that shortens URLs, stores mappings, and handles redirects.  
The service will be instrumented to expose custom performance metrics. Prometheus will be used to collect these metrics, and Grafana will provide dashboards for visualizing the health and usage of the service.  

Technologies used: **Docker, Docker Compose, Prometheus, Grafana, SQLite, Flask/Express**  

---

## Project Objectives
- Develop a fully functional and containerized URL shortener service.  
- Store URL mappings in a lightweight database (SQLite).  
- Expose and monitor custom performance metrics via Prometheus.  
- Build Grafana dashboards to visualize system health and usage patterns.  
- Implement alerting and persistence for reliability.  
- Prepare documentation and final report.  

---

## Project Scope
- **Service Development & Containerization:** Create a URL shortener with POST and GET endpoints, containerized with Docker.  
- **Monitoring Integration:** Instrument the service with Prometheus metrics (success/failed counts, request latency, etc.).  
- **Visualization:** Develop Grafana dashboards for metrics such as request rate, latency, error monitoring.  
- **Alerting & Persistence:** Configure Grafana alerts and Docker volumes to ensure data persistence.  
- **Documentation:** Provide a comprehensive README and API documentation.  

---

## Project Plan [Check details Plan](Tasks%20and%20Plans)

The project will run for **4 weeks**, starting from **_/_/__** and ending on **_/_/__**.  

### **Week 1 (_/_ - _/_): Build & Containerize the URL Shortener**
- **Tasks:**  
  - Develop webservice with POST `/shorten` and GET `/<short_code>` endpoints.  
  - Use SQLite for URL storage.  
  - Write Dockerfile & docker-compose.yml.  
- **Deliverables:**  
  - Functional service running in Docker.  

---

### **Week 2 (_/_ - _/_): Instrumenting with Prometheus**
- **Tasks:**  
  - Add custom metrics (URL created, redirects, errors, latency).  
  - Configure Prometheus to scrape metrics.  
  - Update docker-compose.yml to include Prometheus.  
- **Deliverables:**  
  - Exposed `/metrics` endpoint.  
  - Prometheus collecting and displaying metrics.  

---

### **Week 3 (_/_ - _/_): Visualization with Grafana**
- **Tasks:**  
  - Add Grafana service to the stack.  
  - Connect Grafana to Prometheus.  
  - Build dashboards for key metrics.  
- **Deliverables:**  
  - Grafana dashboard showing service usage & health.  

---

### **Week 4 (_/_ - _/_): Alerting, Persistence & Documentation**
- **Tasks:**  
  - Configure Grafana alerts (e.g., high 404 rate, latency issues).  
  - Add Docker volumes for SQLite, Prometheus, and Grafana data.  
  - Conduct final testing and persistence validation.  
  - Write documentation & finalize report.  
- **Deliverables:**  
  - Fully persistent monitoring stack.  
  - Alerts configured in Grafana.  
  - Final project documentation.  

---
