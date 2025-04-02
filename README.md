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
### Go official document install grafana or got this link
### then run command for Ubuntu and Debian(64 Bit)
```
sudo -i
apt update 
apt upgrade -y
wget -q -O /usr/share/keyrings/grafana.key https://packages.grafana.com/gpg.key
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list

apt update 
apt install -y grafana
systemctl start grafana-server
systemctl enable grafana-server
systemctl status grafana-server
```
##### paste your public_ip:3000 access dashboard 
##### username= admin
##### password= admin

