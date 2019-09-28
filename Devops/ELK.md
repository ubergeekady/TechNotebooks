## Setting up ELK on Ubuntu 19.04 LTS

```
sudo apt update

//For java version 8
sudo apt install openjdk-8-jre

wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list

sudo apt update

sudo apt install elasticsearch

sudo nano /etc/elasticsearch/elasticsearch.yml

. . .
network.host: localhost
. . .

sudo systemctl start elasticsearch

sudo systemctl enable elasticsearch

sudo systemctl status elasticsearch

curl -X GET "localhost:9200"

sudo apt install kibana

sudo systemctl enable kibana

sudo systemctl start kibana

sudo systemctl status kibana

echo "kibanaadmin:`openssl passwd -apr1`" | sudo tee -a /etc/nginx/htpasswd.users

password
password

sudo apt install nginx


server {
    listen 80;

    server_name example.com;

    auth_basic "Restricted Access";
    auth_basic_user_file /etc/nginx/htpasswd.users;

    location / {
        proxy_pass http://localhost:5601;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

nginx -t

systemctl restart nginx

ufw allow 'Nginx Full'
ufw allow ssh

ufw enable
ufw status



//Risky you can expose 9200 by listening on 0.0.0.0 and ufw allow 9200
```

