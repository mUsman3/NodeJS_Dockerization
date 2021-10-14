# NodeJS_Dockerization

1. git clone $repo
2. Navigate into directory 
3. Install docker on your environment if not installed 
4. After install run following command
    • docker build –t nodejs:latest 
    • docker run –name nodejs-con –it –d –p 9876:8080 nodejs:latest
    • docker exec –it nodejs-con sh 
    • whoami 
5. Go to browser and type localhost:9876 
6. It will say “Hello world”
7. Now we are going to use NGINX for Reverse proxy. For this purpose, you have to run the following commands
    • sudo apt-get 
    • sudo apt-get install nginx 
    • sudo systemctl start nginx 
    • sudo nano /etc/nginx/sites-available/default
server_name yourdomain.com www.yourdomain.com;
`location / {    proxy_pass http://localhost:3000;
proxy_http_version 1.1;    
proxy_set_header Upgrade $http_upgrade;    
proxy_set_header Connection 'upgrade';    
proxy_set_header Host $host;    
proxy_cache_bypass $http_upgrade;
}`
    • sudo nginx –t
    • sudo systemctl restart nginx 
    • 
8. Register you domain from any Domain Registrar and configure with your hosting/server
9. Add SSL with letsencrypt
10. sudo add-apt-repository ppa:certbot/certbot
11. sudo apt-get update
12. sudo apt-get install python-certbot-nginx
13. sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
