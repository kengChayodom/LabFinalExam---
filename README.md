![image](https://github.com/user-attachments/assets/1038cdf7-1d5d-4dca-a132-825c967d935c)# LabFinalExam---

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
cd ~ //back to root ก่อน


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

File structure ![image](https://github.com/user-attachments/assets/bc3ddceb-b864-4951-9293-bf9cb2f2388b)

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
![image](https://github.com/user-attachments/assets/0f4e192d-c5b8-4179-8424-8a2ba798eb49)

```
docker run --name {ตั้งชื่าตรงนี้ละก็เอา {} ออกด้วยเช่นตัวอย่างด้านล่างตั้งชื่อว่าmapping} -p 8080:80 -v /var/www/html:/usr/share/nginx/html -d nginx

หรือก็คือ

docker run --name mapping -p 8080:80 -v /var/www/html:/usr/share/nginx/html -d nginx
```


9. The proctor will provide docker-compose.yml file, run the given docker-compose.yml and show the output in the browser
```
docker compose up -d
```

```
services:
  web:
    image: kengchayodom/test
    ports:
      - "8105:80"
```
10.Create a new HTML file in the VM, Write your docker-compose.yml to run your image,
and map the volume to your new HTML file, and show the output.

//back to root folder
```
cd ~ 
```


create new file html
```
touch newindex.html
```


edit file html and write something
```
nano newindex.html
```

check file html

```
 cat newindex.html
```
create docker-compose.html

```
touch docker-compose.yml
```
edit file docker-compose
```
nano docker-compose.yml
```


put this 
```
version: '3'
services:
  web:
    image: nginx
    container_name: my-nginx
    ports:
      - "8080:80"
    volumes:
      - ./newindex.html:/usr/share/nginx/html/index.html
```
then 
```
docker compose up -d
```

open ip with port in docker-compose ##can change port when port is already allocated
![image](https://github.com/user-attachments/assets/11e351bd-14bd-4533-9996-4cb56f5d3e0f)

