    # Monitoring Stack with Prometheus + Grafana + Docker Compose

A full monitoring stack that collects real-time metrics from a Flask application and visualizes them on a live Grafana dashboard — all running in Docker containers.

## What it does

- Flask app exposes a `/metrics` endpoint
- Prometheus scrapes metrics from the app every 15 seconds
- Grafana reads from Prometheus and displays live graphsś
- Everything runs together with one command using Docker Compose

## Tech Stack

- **Python / Flask** — web application with metrics endpoint
- **Prometheus** — metrics collection and storage
- **Grafana** — metrics visualization and dashboards
- **Docker Compose** — multi-container orchestration

## Project Structure

```
monitoring-stack/
├── app/
│   ├── app.py                # Flask app with /metrics endpoint
│   ├── Dockerfile            # App container instructions
│   └── requirements.txt      # Python dependencies
├── prometheus/
│   └── prometheus.yml        # Prometheus scrape config
├── docker-compose.yml        # All containers defined here
└── README.md
```

## How to run

```bash
# Clone the repo
git clone https://github.com/naseeff-7/monitoring-stack
cd monitoring-stack

# Start all containers
docker compose up --build
```

That's it. All 3 services start automatically.

## Access the services

| Service | URL | Credentials |
|---------|-----|-------------|
| Flask App | http://localhost:5000 | - |
| Prometheus | http://localhost:9090 | - |
| Grafana | http://localhost:3000 | admin / admin |

## How monitoring works

```
User visits app → REQUEST_COUNT increments
                         ↓
        Prometheus scrapes /metrics every 15s
                         ↓
         Grafana reads from Prometheus
                         ↓
        Live graph updates on dashboard
```

## Prometheus Query

To see total request count in Prometheus or Grafana:
```
app_requests_total
```

## Key concepts demonstrated

- Multi-container orchestration with Docker Compose
- Application metrics exposure using prometheus-client
- Prometheus scrape configuration
- Grafana data source setup and dashboard creation
- Real-time application monitoring

---

Built by [Naseef](https://github.com/naseeff-7) — BCA Cloud Computing & DevOps
