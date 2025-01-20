### Configuring updates

By default proxmox assumes that you have/will have enterprise licesne assigned. Since I use Proxmox for homelab, I need to configure it to apply updates without the license.
To do that, click on the node:      

![image](https://github.com/user-attachments/assets/77cb45c4-0518-4c2c-a9cc-5c2a940fab89)

Go to the 'Repositories' and deactivate the enterprise repos:    

![image](https://github.com/user-attachments/assets/6596b347-f996-4d08-aa0a-bda298224405)

Once that's done, I can add 'no-subscription' repository that still allows us to do the updates:        

![image](https://github.com/user-attachments/assets/9e190a90-cbb6-46bf-8eee-78d5257c487c)

After adding the repository, go to Updates and click on "Refresh":

![image](https://github.com/user-attachments/assets/fd86e061-05ee-4009-8224-42a96ae50678)

If everything works as intended you should see the updates on the page that you can apply to your node.

![image](https://github.com/user-attachments/assets/89b63a61-e110-44c4-8283-1e0e9b6ec816)

Doing updates this way is equivielent to running an update on your Proxmox node CLI with `app update && apt upgrade`.

![image](https://github.com/user-attachments/assets/fd149f2c-26d1-4d3a-991a-9b0900050556)

#### Possible issues 

There is a change that you may get an error stating that the updates couldn't be downloaded. That is mainly caused by the DNS. Your DNS setting should be pointing to your home network DNS IP rather than 127.0.0.1.

![image](https://github.com/user-attachments/assets/50000a6e-4418-4538-8cba-9dfaace20df0)

#### Enable email notifications  
