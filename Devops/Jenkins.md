## Setting up Jenkins on Ubuntu 19.04 LTS

```
sudo apt install default-jre

wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt update

sudo apt install jenkins

sudo systemctl start jenkins

sudo systemctl status jenkins

sudo ufw allow 8080

sudo ufw allow OpenSSH

sudo ufw enable

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

sudo apt install nginx

sudo ufw allow 'Nginx HTTP'

nano /etc/nginx.conf

        server_names_hash_bucket_size 64; 
```

/etc/nginx/sites-enabled/default

```
server {
       listen 80;
       listen [::]:80;

        server_name jenkins.phoneparloan.online;

        access_log            /var/log/nginx/jenkins.access.log;
        error_log             /var/log/nginx/jenkins.error.log;

        location / {
                #try_files $uri $uri/ =404;
                include /etc/nginx/proxy_params;
                proxy_pass          http://localhost:8080;
                proxy_read_timeout  90s;
                # Fix potential "It appears that your reverse proxy setup is broken" error.
                proxy_redirect      http://localhost:8080 https://jenkins.phoneparloan.online;
        }
}
```

