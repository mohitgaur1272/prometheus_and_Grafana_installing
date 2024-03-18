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
sudo mv prometheus promtool /usr/bin/
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

