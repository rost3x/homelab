#### Configuring updates

By default proxmox assumes that you have/will have enterprise licesne assigned. Since I use Proxmox for homelab, I need to configure it to apply updates without the license.
To do that, click on the node:      

![image](https://github.com/user-attachments/assets/77cb45c4-0518-4c2c-a9cc-5c2a940fab89)

Go to the 'Repositories' and deactivate the enterprise repos:    

![image](https://github.com/user-attachments/assets/6596b347-f996-4d08-aa0a-bda298224405)

Once that's done, I can add 'no-subscription' repository that still allows us to do the updates:        

![image](https://github.com/user-attachments/assets/9e190a90-cbb6-46bf-8eee-78d5257c487c)

#### Enable email notifications  
