### System Health Monitoring Dashboard
A Docker-based system health monitoring stack using **Grafana**, **Prometheus**, and **Node Exporter**.  
Prometheus collects system metrics from Node Exporter, and Grafana visualizes them in a real-time dashboard.

### Setup Steps
##### Create dedicated docker network 
```bash
docker network create system-monitoring
```
##### Create `grafana-storage` folder with proper permissions
```bash
mkdir -p grafana-storage
sudo chown -R 472:472 grafana-storage  # 472 is Grafana's internal user
```
##### Create .env file withthese contents:
```env
GRAFANA_PORT=3000
PROMETHEUS_PORT=9090
NODE_EXPORTER_PORT=9100
GRAFANA_ADMIN_PASSWORD=your_password
```
You can modify the port values as needed. These are the defaults.
##### Start the monitoring stack
```bash
docker-compose up -d
```
##### Access the dashboards
1. `http://localhost:9090` : Prometheus Interface
2. `http://localhost:3000` : Grafana Interface
Login with user admin and the password you set in .env
##### Import the Grafana dashboard
- Go to dashboards and click on "create dashboard" and then on "import a dashboard"
- Enter Dashboard ID 1860, then click Load(1860 is a public dashboard available online)
- Set the data source to your Prometheus instance and click Import

#### You now have a live Grafana System Hardware Dashboard!
