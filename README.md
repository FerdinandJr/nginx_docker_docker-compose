# Get Started with NGINX: use nginx as webserver, reverse proxy and load balancer


## Install Nginx Ubuntu


1. Install Nginx:

```bash
sudo apt update
```

```bash
sudo apt install nginx
```

```bash
sudo systemctl start nginx
```

```bash
sudo systemctl enable nginx
```

```bash
sudo systemctl status nginx
```

### Nginx as Web Server

1. Create index.html file and paste a html code file:

```bash
sudo nano -p /var/www/html/index.html
```

2. Paste your index.html code:

3. Restart nginx:

```bash
sudo systemctl restart nginx
```

### Nginx as Reverse Proxy

1. Install node.js:

```bash
sudo apt install curl
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo bash - 
sudo apt install -y nodejs
```

2. Create a Node.js Application:

```bash
sudo mkdir /var/www/myapp
```

```bash
cd /var/www/myapp
```

```bash
sudo npm install express
```

```bash
sudo npm init -y
```

```bash
sudo nano index.js
```

Paste the sample index.js file above:

3. Run the Node.js application:

```bash
node index.js
```

Your Node.js application should now be running on port 3000. You can test it by navigating to http://your-server-ip:3000

### Configure Node.js file to run Nginx as reverse proxy


1. Configure default file

```bash
sudo nano /etc/nginx/sites-available/default
```

1. Paste the configuration in server part

```bash
location / {
        proxy_pass http://localhost:3000;  # Proxy to Node.js app on port 3000
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```

#### Configure Node.js file to run in pm2

1. Install pm2

```bash
sudo npm install -g pm2
```
2. Run Node.js using pm2:

```bash
pm2 start app.js --name "myapp"
```

3. Stop the previous nginx running in the port 3000

```bash
sudo lsof -i :3000
```

```bash
sudo kill -9 1234
```

1234 = PID number

4. Restart pm2 myapp and nginx

```bash
sudo pm2 restart myapp
```

```bash
sudo systemctl restart nginx
```

### Nginx as Load Balancer