# PROJECT-8

Configure Apache As A Load Balancer


Configure load balancing

![image](https://user-images.githubusercontent.com/113097621/217114598-58ec7d45-2856-4aea-b217-736f60d6a818.png)

![image](https://user-images.githubusercontent.com/113097621/217114703-aed4352d-18c4-4e74-8a10-4d028b797992.png)


To access your LB’s public IP address or Public DNS name from your browser:

http://54.85.215.79/index.php

![image](https://user-images.githubusercontent.com/113097621/217123807-c69daa90-a1ab-470d-8d70-a01143534e82.png)

Open two ssh/Putty consoles for both Web Servers and run following command:


sudo tail -f /var/log/httpd/access_log

//user-images.githubusercontent.com/113097621/217115448-54e4c7e1-293f-467f-acc4-aa8f7d757ff7.png)


Open two ssh/Putty consoles for both Web Servers and run following command:
sudo tail -f /var/log/httpd/access_log
Webserver 1
![image](https://user-images.githubusercontent.com/113097621/217116241-3933efad-1192-43a9-a991-bc79042d1aa6.png)

webserver 2
![image](https://user-images.githubusercontent.com/113097621/217116510-d0069f3c-8a2f-4772-92f5-4bf33a43bfca.png)

Configure Local DNS Names Resolution
sudo vi /etc/hosts
<WebServer1-Private-IP-Address> Web1
<WebServer2-Private-IP-Address> Web2

![image](https://user-images.githubusercontent.com/113097621/217119827-efc3a85f-5d5b-4fac-9d88-38a2d0bc1122.png)

Update LB config file with those names instead of IP addresses
BalancerMember http://Web1:80 loadfactor=5 timeout=1
BalancerMember http://Web2:80 loadfactor=5 timeout=1
 
sudo vi /etc/apache2/sites-available/000-default.conf
![image](https://user-images.githubusercontent.com/113097621/217120490-b78347be-14f9-48c9-9499-a635a189e21c.png)
  
You can try to curl your Web Servers from LB locally curl http://Web1 or curl http://Web2 
![image](https://user-images.githubusercontent.com/113097621/217121182-cd38e731-17ad-47a6-be95-c6a357f38bd5.png)
  
 ![image](https://user-images.githubusercontent.com/113097621/217121620-1fef7a3a-7b38-44e7-9db3-978a00589017.png)





