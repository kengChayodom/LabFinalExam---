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
![image](https://github.com/user-attachments/assets/4f39ee4a-de88-4785-b919-c25beb11f35a)

```

sudo usermod -aG root ubuntu
sudo chmod -R 775 /var/www/html

exit => login again

cd /var/www/html
touch index.html
vi index.html

then test
```
4. Install Docker in the virtual machine, and call the hello-world image to run
![image](https://github.com/user-attachments/assets/8d59d92d-64b4-46de-b603-947d905c899d)
```
curl -fsSL https://get.docker.com/ -o get-docker.sh
sudo sh get-docker.sh
//download docker

sudo usermod -aG docker ubuntu
exit then login again

docker container run hello-world
```
5. Run the Docker image Nginx and show the default page
![image](https://github.com/user-attachments/assets/3e98e76c-14c8-49d9-8bd0-ebbf00665498)
```
docker run -p 8100:80 nginx
```

6. The proctor will send you the HTML file, create a new image to show the HTML file you received, and then run the container to show the output image in the VM
![image](https://github.com/user-attachments/assets/a1fe4ba2-825d-4851-9ae8-010bd8bd2b62)

create Dockerfile
```
FROM nginx:latest

COPY ./html /usr/share/nginx/html

EXPOSE 80
```

build docker 
```
docker build -t kengchayodom/labtesttest .
```

7. Push the image you have created to your Docker Hub
```
docker push kengchayodom/labtesttest
```

back to 6 run the container to show the output image in the VM
![image](https://github.com/user-attachments/assets/24baec33-3bd0-4fa4-951c-a4025e036a3e)

```
in vm

docker pull kengchayodom/labtesttest

docker run -p 8101:80 kengchayodom/labtesttest

```

8. With your Docker image, map the volume of your container to show the website youhave done on question no. 3



10. Push the image you have created to your Docker Hub
