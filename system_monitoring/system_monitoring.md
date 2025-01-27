### Grafana     

I could write up a long guide how to set up Grafana on a server, however, the original [documentation](https://grafana.com/docs/grafana/latest/setup-grafana/) does a fantastic job explaining how to do it.      

Once Grafana is set up on your server, you should be able to access it through `http://localhost:3000` or `serverIP:3000` (assuming that you used a default port). You will be prompted to enter the credentials.        

Default username: admin     
Default password: admin     

![image](https://github.com/user-attachments/assets/8d265dce-9d95-4993-a4e2-e5fd24601ac7)

Once you sign in, you'll be prompted to change the password. 

### Node Exporter

I felt like the official documentation that's meant to help with the instalation of the Node Exporter isn't completed.      
I've had to do a little bit of digging on how to configure the systemd target correctly to make it work on a Ubuntu server.     

This is how it went.        
I downloaded the latest version of the node exporter following the official instructions:
`wget https://github.com/prometheus/node_exporter/releases/download/v<VERSION>/node_exporter-<VERSION>.<OS>-<ARCH>.tar.gz       
tar xvfz node_exporter-*.*-amd64.tar.gz`

Filling out the the "VERSION" and "OS - ARCH" with the one that I needed.       

Then I moved the untared directory to `/usr/bin/local/`     

The next step was to create the service account and the systemd service       

`sudo useradd -rs /bin/false node_exporter`     

`sudo vim /etc/systemd/system/node_exporter.service`        

`[Unit]     
Description=Node Exporter       
After=network.target        

[Service]       
User=node_exporter      
Group=node_exporter     
Type=simple     
ExecStart=/usr/local/bin/node_exporter --web.config=/etc/prometheus_node_exporter/configuration.yml     

[Install]       
WantedBy=multi-user.target`     
