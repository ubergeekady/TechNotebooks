Install Ansible on the controller system. If you don't specify an inventory file, Ansible will use the default inventory file - /etc/ansible/hosts

```
server1.company.com
server2.company.com

[mail]
server3.company.com
server4.company.com

[db]
server5.company.com
server6.company.com

[all_servers:children]
mail
db
web
```

Sample inventory file

```
web ansible_host=server1.company.com ansible_connection=ssh ansible_port=22 ansible_user=sss ansible_ssh_pass
```

```
ansible target1 -m ping -i inventory.txt
```

