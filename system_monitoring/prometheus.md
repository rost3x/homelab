### Prometheus setup        

Download and extract the latest (or desired) version of prometheus from the [official website](https://prometheus.io/).

To begin the setup of prometheus on the server, create a service account.       

`sudo useradd -rs /bin/false prometheus`        

Then add two directories.       

```
sudo mkdir /etc/prometheus        
sudo mkdir /var/lib/prometheus
```     

Next navigate to the extracted prometheus directory and move the directories.       

Binary files        
```
sudo mv prometheus /usr/local/bin       
sudo mv promtool /usr/local/bin     
```     

And then the rest       
```
sudo mv console* /etc/prometheus        
sudo mv prometheus.yml /etc/prometheus      
```

Change the ownership on the directories.        
```
sudo chown prometheus:prometheus /usr/local/bin/prometheus 
sudo chown prometheus:prometheus /usr/local/bin/promtool 
sudo chown prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /etc/prometheus/console*
sudo chown -R prometheus:prometheus /var/lib/prometheus
```

Modify the configuration file.      

`sudo vim /etc/prometheus/prometheus.yml`       

Since I try to keep majority of configuration as default, I just add the node_exporter at the bottom of the config file.      

```
- job_name: 'node_exporter'
  static_configs:
    - targets: ['localhost:9100']
```



