## Getting MongoDB working on EC2

Sources : https://docs.mongodb.com/ecosystem/platforms/amazon-ec2/#deploy-mongodb-ec2  
https://docs.mongodb.com/v3.2/tutorial/install-mongodb-on-amazon/

```
echo "[mongodb-org-3.2]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/amazon/2013.03/mongodb-org/3.2/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.2.asc" |
  sudo tee -a /etc/yum.repos.d/mongodb-org-3.2.repo
```

```sudo yum -y update && sudo yum install -y mongodb-org```

```sudo service mongod start```

Some observations/difficulties for connecting

* Had to open up inbound port 27017 on instance (dashboard -> security groups -> edit whichever group you're using)
* Also had to modify `/etc/mongo.conf` - set the bindIP to 0.0.0.0 (for all IP addresses). Not sure about this, but don't think commenting the line worked.
* Had to fiddle with permissions (`chmod`) to edit some files.

To connect via SSH, used port forwarding:

This is a good resourse: https://www.digitalocean.com/community/tutorials/how-to-securely-configure-a-production-mongodb-server

`ssh -i ~/.ssh/amazon_SSH_key_pair -L 9000:localhost:27017 ec2-user@35.161.14.209`

Then on local computer:

`mongo locahost:9000`

Also had to use AWS IP, rather than DNS name in SSH command above - I think this is because VPN was switched on.

This was helpful too: http://serverfault.com/questions/597765/how-to-connect-to-mongodb-server-via-ssh-tunnel



