# Ubuntu 16.04 Virtual Machine
This VM took a long time to set up and often has issues come up. This is where I will record the errors, settings, and guides for my ubuntu 16.04 virtual machine.

***
***

If your VM stops in the middle of a restart with this on the screen: 
```
/dev/sda1: UNEXPECTED INCONSISTENCY: run fsck manually
```
type in:
```
fsck /dev/sda1
```
and type in `y` whenever it says `Fix<y>?`

***
***

### The network wasn’t working - Solution:
First, restart the virtual machine and see if that fixes it.

Go to Mac’s system settings > Network to see what the current IP address is.

![linux-1](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-1.png)

![linux-2](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-2.png)

Go into the VM settings > Network > Options (bottom right corner) 

![linux-3](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-3.png)

![linux-4](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-4.png)

 Go to the IPv4 Settings tab and make sure that both the gateway and DNS Servers info matches the mac’s IP address. If not, change it. Also, make sure the address matches the ip addr given when you query ip addr in the vm terminal. (I think. If the command isn’t working, then you are out of luck, I guess...)

 ![linux-5](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-5.png)

Also, go to the setting of the virtual machine (from VMware Fusion itself) and make sure that under ‘Network Adapter’, the option ‘Share with my Mac’ is the one checked.
 
 ![linux-6](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-6.png)

 ![linux-7](https://github.com/ryancj14/LinkToTheNow/wiki/Images/Linux-7.png)
 
 ***

Use ‘hostname -I’ command to see IP address within the virtual machine.
 
***

In the `vi` editor, my arrow keys were printing letters. I used `sudo apt-get install vim` and then it stopped doing that.

But I think this is actually the better answer:

To disable printing letters on pressing arrows in edit mode you can do following
```
vi $HOME/.exrc 
```
(create file if it does not exist) and then add line `set nocompatible` to it and save.

***

----------------------------------
Initially created by Ryan Johnson, June 2020.