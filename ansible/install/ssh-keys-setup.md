### create a user on all machines ( controller & all targets )

	useradd ananya -m -d /home/ananya -s /bin/bash

### add user to sudoers for root previliges  on all machines ( all targets )

	echo -e 'ananya  ALL=(ALL)  NOPASSWD:  ALL' > /etc/sudoers.d/ananya

### genereate ssh keys for above user on contrller machine 

```
	1) switch to user ( su - ananya )
	2) run "ssh-keygen" command as user ( this will genereate ssh keys for the user ) 
```
```
        on ansible controller machine
		cd /home/ananya/.ssh 
		cat id_rsa.pub (copy the content)
		sudo systemctl restart sshd
```
### copy user ssh keys from ansible contrller to all target hosts

```
	1) on all target machines
		   swith to the user ( su - ananya )
		   mkdir -p /home/ananya/.ssh
		   touch /home/ananya/.ssh/authorized_keys
		   chmod -R 700 /home/ananya/.ssh
		   vi /home/ananya/.ssh/authorized_keys  (enter the copied contet of id_rsa.pub from controller & save the file)
		   sudo systemctl restart sshd

```	
	

