From my mac, I ssh into my virtual machine with one of this command:
```bash
ssh student@192.168.248.129
```
The number corresponds to the IP address on my virtual machine, and the ‘student’ is the username.
Hint: run `hostname -I` in the virtual machine to get the ip address.

***

### Set Up SSH Keys So You Don't Have to Always Log In When Accessing a Remote Machine
Using SSH keys you can make it so each time you want to 'ssh' to or 'scp' to/from a remote machine you don't have log in again. In essence it creates a cryptographic key that the two machines use to authenticate each other. Here is how:
 
On the remote machine:
```bash
cd ~
mkdir .ssh
```
From your own machine:
```
ssh-keygen -t rsa -b 4096
``` 
You can leave all the prompted fields blank. 

This will create a public (id_rsa.pub) and private (id_rsa) key. The public key can be shared with remote machines, Github, etc (as we will do next), but the private key should remain secret. With the private key, someone could log in as you.

If file .ssh/authorized_keys does not exist on the remote machine (the common case), just copy the generated key you just generated to the remote machine:
```
scp ~/.ssh/id_rsa.pub username@remoteMachine.edu:~/.ssh/authorized_keys
```
If authorized_keys does exist on the remote machine you will just want to append your new key to that file:
```
cat ~/.ssh/id_rsa.pub | ssh username@remoteMachine.edu "cat - >> ~/.ssh/authorized_keys"
```
Now you can copy things over to a remote machine without specifying a password, as in:
```
scp someFileOnMyMachine someuser@remoteMachine.edu:targetLocation
```
or
```
scp someuser@remoteMachine.edu:someRemoteFile targetLocationOnMyPC
```
And, if you have the same username on both the local and remote machines, then you don't even need to specify the someuser@ part in the above commands (it will just fill it in for you).

Using the above you can also easily log into the remote machine as in ssh remoteMachine.edu. Once you log in to the remote machine, you can always close the connection with ^D (control-D).

#### ssh

Open a "shell" or command line on a remote machine as in:
```
ssh 192.168.52.23  # Specify machine by IP address
ssh bluebell # Specify machine by a name
```

This is how you "log in" to a remote machine.
scp
Copy files to and from a remote machine as in:
```
### Copy file1 from my machine to the Downloads directory on another machine
scp file1 student@192.168.52.23:Downloads

### Copy the .bashrc file from remote machine to /tmp on my machine
scp username@hostname:.bashrc /tmp
```

This is how you move files between machines.

***

SSH CONFIG
You can create an SSH Config file in order to save SSH preferences. This file is located at ~/.ssh/config. Each entry in this file lists a remote machine that you can connect to by alias.

For example, to connect to the CAEDM SSH server by only running ssh caedm you would add an entry to the file like this:

```
Host caedm
    Hostname ssh.et.byu.edu
    User cosmo
```

### Errors

1. When my ssh stopped working, I just deleted the .ssh folders in both my local and virtual machines and then restarted the keymaking and sharing process. And I'm happy to say that it worked!

2. SSH connection stopped working, but only for VS Code (Remote-SSH). The solution was to `rm -rf ~/.vscode-server` on the remote Linux server.

----------------------------------
Initially created by Ryan Johnson, June 2020.