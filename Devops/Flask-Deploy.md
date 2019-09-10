New linode machine. Rootpassword

```
apt update && apt upgrade
hostnamectl set-hostname playstoreapp
hostname

nano /etc/hosts
```

```
127.0.0.1       localhost

172.105.54.8    playstoreapp
```

```
adduser aditya
appyfizz
adduser aditya sudo

relogin as aditya
```

```
sudo apt install ufw
sudo ufw default allow outgoing
sudo ufw default deny incoming
sudo ufw allow ssh
sudo ufw allow 5000
sudo ufw enable
sudo ufw status
```

```
sudo apt install python3-pip
sudo apt install python3-venv
sudo apt install virtualenv
sudo apt install nginx
```

```
mkdir playstorescrapper
cd playstorescrapper
virtualenv venv -p python3
source venv/bin/activate
git clone <repo_url>
cd playstorescrapper
pip install -r requirements.txt
```

```
pip install gunicorn
```

```
sudo rm /etc/nginx/sites-enabled/default
sudo nano /etc/nginx/sites-enabled/playstoreapp
```

```
server {
        listen 80;
        server_name IP/DOMAIN;

    location / {
        proxy_pass http://localhost:8000;
        include /etc/nginx/proxy_params;
        proxy_redirect off;
    }
}
```

```
sudo ufw allow http/tcp
sudo ufw delete allow 5000
sudo ufw enable
sudo systemctl restart nginx
```

```
(venv) aditya@playstoreapp:~/playstorescrapper/playstorescrapper$ python
Python 3.7.3 (default, Aug 20 2019, 17:04:43) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from playstorescrapperapp import db
>>> db.create_all()
>>> exit()
```

```
python seed_data.py
```

```
gunicorn -w 3 run:app
Ctrl+C
```

```
sudo apt install supervisor
```

```
sudo nano /etc/supervisor/conf.d/playstoreapp.conf
```

```
[program:playstoreapp]
directory=/home/aditya/playstorescrapper/playstorescrapper
command=/home/aditya/playstorescrapper/venv/bin/gunicorn -w 3 run:app
user=aditya
autostart=true
autorestart=true
stopasgroup=true
killasgroup=true
stderr_logfile=/var/log/playstoreapp/playstoreapp.err
stdout_logfile=/var/log/playstoreapp/playstoreapp.out
```

```
sudo touch /var/log/playstoreapp/playstoreapp.err
sudo touch /var/log/playstoreapp/playstoreapp.out
sudo supervisorctl reload
```

