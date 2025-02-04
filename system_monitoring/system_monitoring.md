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

Then I moved the `node_exporter` executable file that was in the tar directory to `/usr/bin/local/`     

The next step was to create the service account and the systemd service       

`sudo useradd -rs /bin/false node_exporter`     

`sudo vim /etc/systemd/system/node_exporter.service`        

```
[Unit]     
Description=Node Exporter       
Wants=network-online.target     
After=network-online.target        

[Service]       
User=node_exporter      
Group=node_exporter     
Type=simple     
ExecStart=/usr/local/bin/node_exporter     

[Install]       
WantedBy=multi-user.target
```     

Now that the systemd service was created I could run it.        
`sudo systemctl enable --now node_exporter.service`     

If everything if configured correctly, this is what you should see.    

![image](https://github.com/user-attachments/assets/91df3312-d6c6-4c22-9666-de9d1c5fd703)

**Depending on the system that you use, you may need to allow default port (9100) to be allowed on the firewall. In my case I've had to do it before I ran any node_exporter.**     

`ufw allow 9100`

**If you ran node_exporter before allowing port 9100 on your firewall, kill the process, allow the port and try running it again**

