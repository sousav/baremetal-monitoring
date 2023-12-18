# SSH Config
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