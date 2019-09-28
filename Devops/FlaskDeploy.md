New linode machine. Rootpassword

```
apt update && apt upgrade
hostnamectl set-hostname playstoreapp
hostname

nano /etc/hosts
```

```
127.0.0.1       localhost

<MACHINEIP>    playstoreapp
```

```
adduser aditya
<PASSWORD>
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
        server_name <IP/DOMAIN>;

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
sudo nano /etc/supervisor/conf.d/creditriskapp.conf
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
mkdir /var/log/creditriskapp
sudo touch /var/log/creditriskapp/creditriskapp.err
sudo touch /var/log/creditriskapp/creditriskapp.out
sudo supervisorctl reload
```

## Database

```
sudo apt install postgresql postgresql-contrib
sudo -u postgres createuser --superuser aditya
sudo -u aditya createdb playstoredb

sudo -i -u postgres
postgres@playstoreapp:~$ psql
psql (11.5 (Ubuntu 11.5-0ubuntu0.19.04.1))
Type "help" for help.

postgres=# \du
postgres=# ALTER USER aditya WITH PASSWORD '<DBPASSWORD>';
postgres=# grant all privileges on database playstoredb to aditya;

export PLAYSTORESCRAPPERAPP_DATABASEAPPURL="postgresql://aditya:<DBPASSWORD>@localhost/playstoredb"
```

NOTE - There is some problem here needs to be fixed. Sometimes you might have to paste the DB url into the init.py file or make it load it from a file and place the file in /etc/settings place.

## For PGAdmin

```
sudo ufw allow 5432
sudo ufw enable
```

```
Add or edit the following line in your postgresql.conf :

listen_addresses = '*'

Add the following line as the first line of pg_hba.conf. It allows access to all databases for all users with an encrypted password:

# TYPE DATABASE USER CIDR-ADDRESS  METHOD
host  all  all 0.0.0.0/0 md5

Restart Postgresql after adding this with service postgresql restart or the equivalent command for your setup.
```


