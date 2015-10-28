
#### Passwordless SSH with identites

There are 2 machines, machine_1 want connect through ssh to machine_2. Normally you should type something like ssh user@ip-addres and then put there password but we want it passwordless. So first step - create RSA key-pair

```bash
ssh-keygen -t rsa
```

copy key to the server

```bash
cat .ssh/id_rsa.pub | ssh user@ip-address 'cat >> .ssh/authorized_keys'
```

from now you should be able to log in to machine_2 through

```bash
ssh -i ~/.ssh/related_private_key user@ip-address
```

we can make it more better, create/edit a config file for ssh - ~/.ssh/config and put 

```bash
Host host_name
    HostName ip-address
    User user
    Port port
	IdentityFile ~/.ssh/related_private_key
```

Now you can connect with 

ssh host_name 

So, block any other types of authentication
vim /etc/ssh/sshd_config
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
and restart service
service ssh restart
Sources:
[[1]](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-keys-with-digitalocean-droplets), 
[[2]](http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/), 
[[3]](http://derekbarber.ca/blog/2012/02/13/debugging-public-key-authentication/)
