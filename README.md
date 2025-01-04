# Get Started with NGINX: use nginx as webserver, reverse proxy and load balancer


## Install Nginx Ubuntu


1. Install Nginx

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

1. Create index.html file and paste a html code file

```bash
sudo nano -p /var/www/html/index.html
```

2. Paste your index.html code

3. Restart nginx

```bash
sudo systemctl restart nginx
```

### Nginx as Reverse Proxy

### Nginx as Load Balancer