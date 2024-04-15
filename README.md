# Grafana_installing
## Go official document install grafana or got this link 
```
https://grafana.com/grafana/download
```
## then run command for Ubuntu and Debian(64 Bit)
```
sudo apt-get install -y adduser libfontconfig1 musl
```
```
wget https://dl.grafana.com/enterprise/release/grafana-enterprise_10.4.2_amd64.deb
```
```
sudo dpkg -i grafana-enterprise_10.4.2_amd64.deb
```
## after run this command you will see output like this 
```
### NOT starting on installation, please execute the following statements to configure grafana to start automatically using systemd
 sudo /bin/systemctl daemon-reload
 sudo /bin/systemctl enable grafana-server
### You can start grafana-server by executing
 sudo /bin/systemctl start grafana-server
Processing triggers for systemd (245.4-4ubuntu3.23) ...
```
## so copy this command and run for grafana server start,enable and status
```
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable grafana-server
sudo /bin/systemctl start grafana-server
sudo /bin/systemctl status grafana-server
```
