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
