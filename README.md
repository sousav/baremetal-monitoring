# SSH Config

Grafana/Prometheus monitoring dashboard with NodeExporter and Blackbox data feeds

## Step 1
Launch the containers
```
docker compose up -d
```

## Step 2
Add this config in your ~/.ssh/config

```
Host WS
	Hostname 127.0.0.1  # To Change to your server config
	User root
	IdentityFile ~/.ssh/id_rsa

	# Port forwarding of internal docker subnetwork

	# Grafana
	LocalForward 3000 172.18.0.2:3000

	# Prometheus
	LocalForward 9090 172.18.0.3:9090

	# Node Exporter
	LocalForward 9100 172.18.0.4:9100

	# Blackbox
	LocalForward 9115 172.18.0.5:9115
```

## Step 3
Open an ssh session to the machine
```
ssh WS
```

## Step 4
The differents dashboard are now accessible using localhost

- [Grafana](http://localhost:3000/)
- [Prometheus](http://localhost:9090/)
- [Node Exporter](http://localhost:9100/metrics)
- [BlackBox](http://localhost:9115/metrics)

## Step 5
The default grafana credentials are admin/password, don't forget to change it