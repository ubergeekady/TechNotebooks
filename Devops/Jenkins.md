## Setting up Jenkins on Ubuntu Box

```
Create new Ubuntu 19.0 LTS box on Linode
https://pkg.jenkins.io/debian-stable/

wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

Then add the following entry in your /etc/apt/sources.list:
deb https://pkg.jenkins.io/debian-stable binary/

sudo apt-get update && sudo apt-get upgrade
sudo apt install default-jre
sudo apt-get install jenkins
systemctl status jenkins

Password
cat /var/lib/jenkins/secrets/initialAdminPassword
```

