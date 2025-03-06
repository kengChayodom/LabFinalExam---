# LabFinalExam---

1. Create a virtual machine
   ```
   create instance
   ```

2. Install Nginx (not using Docker) to the virtual machine and show the default home page.
   ![image](https://github.com/user-attachments/assets/29b7123e-1966-4267-bec9-95c775452e38)
```
sudo apt update
sudo apt install nginx

and then run on ip only
if cannot run type
systemctl status nginx
```
3. Edit the HTML to show the new index.html in the Nginx
```
cd /var/www/html

sudo usermod -aG root ubuntu
sudo chmod -R 775 /var/www/html

exit

touch index.html
vi index.html
```
