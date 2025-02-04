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

#### Setup notifications        

I chose to receive any alerts to my Discord channel.        
Discord allows you to create a server for free that you can use for communication with others, however, it also allows you to connect it to various services to provide alerts. Here is how I've done it with Proxmox.      

Click on the Datacenter and scroll all the way down to Notifications. By default you will see "mail-to-root", however, it doesn't send the notifications anywhere since the root email doesn't exist.       

![image](https://github.com/user-attachments/assets/437e9cdd-863f-4f91-9836-2e875237c365)

Next, click on "Add" and select "Webhook". Here you need to enter your Discord channel webhook details followed by "Headers", "Body" and "Secrets".

![image](https://github.com/user-attachments/assets/3ec61325-9b4c-4f04-acff-6b39271789d8)

Once that's completed, you should be able to select it and send a test message. If everything was typed in correctly, you will get a notification on your channel.

![image](https://github.com/user-attachments/assets/bba6d688-8c0f-4fb4-b9f9-cfc93a274ade)

![image](https://github.com/user-attachments/assets/b16fdfef-8ea3-44ad-ab50-cf9d0085999b)

Another important thing is to change your Notification Matchers, as again, by default it is directed to "mail-to-root".

![image](https://github.com/user-attachments/assets/4709adcb-0724-42b5-948f-12b4cc326bd5)

![image](https://github.com/user-attachments/assets/83925e59-75ba-4766-8f66-87afb780911b)

This is just a basic notifications setup. You can go into more details by adding specific "Notification Matchers" or perhas setting up Notifications to go to your email. I chose Discord as it keeps it separate from my already swamped mailbox.

#### Upload OS ISO      

To deploy your first VM you'll need to upload the ISO first to your Proxmox hypervisor.     

There are two ways to do that.      
    - You can upload an ISO image from your machine.        
    - You can upload an ISO directly from a URL link.       

Expand your cluster and naviate to the local storage. There you can select "ISO Images", that's where we will upload the file.     

![image](https://github.com/user-attachments/assets/db279d6c-0f78-47b2-b37e-38dfe54da580)

Now you have a choice of either "Upload" or "Download from URL".      

![image](https://github.com/user-attachments/assets/e8db7b49-471d-479d-b637-3776e0bccffb)

In my case I decided to upload the images from my local machine as I already had the images downloaded.     

![image](https://github.com/user-attachments/assets/ffb46eac-46af-4920-b7fb-1362a6406482)
