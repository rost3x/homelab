#### Configuring updates

By default proxmox assumes that you have/will have enterprise licesne assigned. Since I use Proxmox for homelab, I need to configure it to apply updates without the license.
To do that, click on the node:      

Go to the 'Repositories' and deactivate the enterprise repos:       

Once that's done, I can add 'no-subscription' repository that still allows us to do the updates:        



#### Enable email notifications  
