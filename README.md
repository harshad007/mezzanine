# mezzanine
mezzanine project in dockerised container on aws

To implement this project in existing aws environment do following steps

Setup instructions:

git clone https://github.com/harshad007/mezzanine.git
mv mezzanine/* ./

For creating aws instances 
	Do following changes in code

/roles/addec2/tasks/main.yml
	    vars:
      instance_type: t2.micro
      security_group: default # Change the security group name here
      image: YOUR_AMI_ID #change the AMI, from which you want to launch the server
      region: us-west-2 # Change the Region
      keypair: YOUR_KEY # Change the keypair name
      count: 2 

Note: Setup password-less between newly created server.

ssh-keygen

ssh-copy-id  user@SERVER_IP
-------------------------------------------------------------------------------------------------- 

ansible-playbook startupscript.yml

Now For load balancer

	Do following:
	In group_vars directory change
	server1: IP1 <aws ip from hosts file under group webserver>
	server2: IP2 <aws ip from hosts file under group webserver>

asnible-playbook load-balancer_haproxy.yml 

For mezzanine project setup

ansible-playbook mezzanine.yml

For nagios Monitoring

ansible-playbook nagios.yml
