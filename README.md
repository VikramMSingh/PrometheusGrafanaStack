cat > README.md << 'EOF'
# Prometheus + Node Exporter — Native Install

Observability stack installed natively via systemd. No Docker.

## Stack
- Prometheus v2.54.1
- Node Exporter v1.8.2
- Ubuntu 22.04 (Multipass VM)

## Setup
```bash
# Create users
sudo useradd --no-create-home --shell /bin/false prometheus
sudo useradd --no-create-home --shell /bin/false node_exporter

# Copy config files from this repo
sudo cp prometheus.yml /etc/prometheus/prometheus.yml
sudo cp prometheus.service /etc/systemd/system/
sudo cp node_exporter.service /etc/systemd/system/

# Start services
sudo systemctl daemon-reload
sudo systemctl enable --now prometheus node_exporter

