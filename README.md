# prometheus_installing
### create ec2 instance with image ubuntu  and install prometheus
```
sudo wget https://github.com/prometheus/prometheus/releases/download/v2.51.0-rc.0/prometheus-2.51.0-rc.0.linux-amd64.tar.gz
```
### do untar your tar file 
```
tar xvzf prometheus-2.51.0-rc.0.linux-amd64.tar.gz
```
### then go in this folder 
```
cd  prometheus-2.51.0-rc.0.linux-amd64
```
### if you are use prometheus for testing so run this command 
```
./prometheus
```
### and paste your ```public_ip:9090``` on browser this is by defauly port of prometheus

## and if you are use this tool in industry so follow given steps

### move this file in /usr/bin/ folder for make executable any where in terminal 
```
sudo mv promtool /var/local/bin/promtool
sudo mv prometheus /usr/local/bin/
```
### now create prometheus user and group for run this service by only this user
```
sudo groupadd prometheus
sudo useradd -s /sbin/login/ -g prometheus prometheus   
```
now create folder for save data of server metrix 
```
sudo mkdir /var/lib/prometheus
sudo mkdir /etc/prometheus
sudo mv console_libraries consoles prometheus.yml /etc/prometheus/
```
### give permission prometheus user and group of /etc/prometheus folder 
```
sudo chown -R prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /var/lib/prometheus
sudo chown -R prometheus:prometheus /usr/local/bin/
sudo chown -R prometheus:prometheus /var/local/bin/promtool
```
### now if you want to start and enable by this command systemctl prometheus like docker and apache2 so you have to do create 
### file in systemd folder so run this command 
```
cd /etc/systemd/system
sudo touch prometheus.service
sudo vim prometheus.service
```
```
[Unit]
Description=Prometheus Monitoring
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
group=prometheus
Restart=on-failure

# Location of the prometheus executable
ExecStart=/usr/local/bin/prometheus \
  --config.file=/etc/prometheus/prometheus.yml \
  --storage.tsdb.path=/var/lib/prometheus/

[Install]
WantedBy=multi-user.target
```
### now run this commnad for undestand to system-daemon that i have added one more service so run this 
```
sudo system daemon reload
sudo systemctl start prometheus
sudo systemctl status prometheus
sudo systemctl status prometheus
```
# node_exporter installing on other instance and connect with prometheus server 
```
sudo wget https://github.com/prometheus/node_exporter/releases/download/v1.7.0/node_exporter-1.7.0.linux-amd64.tar.gz
```
```
sudo tar xvzf node_exporter-1.7.0.linux-amd64.tar.gz
cd node_exporter-1.7.0.linux-amd64
```
### now add node_exporter in /usr/local/bin/
```
sudo mv node_exporter /usr/local/bin/
node_exporter --version
```
```
sudo groupadd node_exporter
sudo usermod -s  /sbin/nologin -g node_exporter node_exporter 
```
```
sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter
```
```
cd /etc/systemd/system
sudo touch node_exporter.service
```
```
put data
```
```
sudo systemctl daemon reload 
sudo systemctl start node_exporter
sudo systemctl enable node_exporter
sudo systemctl status node_exporter
```
### now add the node_exporter with prometheus server so go  prometheus server and 
```
sudo vim/etc/prometheus/prometheus.yaml
```
and add the node_exportet in target and sanve file then restart prometheus service 
