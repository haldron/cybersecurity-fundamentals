# Workshop 1: Installing and Becoming Familiar with Kali Linux

## Initial Setup
1. Download and install Virtualbox
2. Get the ova virtualbox image and use directly in virtualbox
3. Username is root and password is root - **Change password*** by using ```passwd``` in the command line and follow the prompts
4. It is not a good idea working as the root user so use the following commands to add your own user
```
adduser -username-
(follow the prompts)
usermod -a -G sudo -username-
```

5. Setup the SSH server in Kali to configure it to run automatically
```
systemctl start ssh
systemctl enable ssh
```

Confirm that sshd is running using the following commands
```netstat -antp | grep sshd```
```systemctl status ssh```
```ps auxf | grep ssh```

6. Download OpenVPN configuration use it inside the fole with the following commands -
To make initial connection to VPN environment -
```openvpn --config hacklab.ovpn```


7. Open a new terminal and add 8.8.8.8 as a new name server to /etc/resolv.conf file
```nano /etc/resolv.conf```
and add the following lines -
nameserver 8.8.8.8
nameserver 10.40.3.1
nameserver 10.40.3.2

8. Install OpenVPN module for Gnome network manager
```sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome```

9. End the VPN connection in the terminal using Ctrl+C
10. Open Network Settings in the OS and add a new VPN connection. Click on *Import from File* and select the .ovpn file
11. Add the VPN to import and close the manager. Now go to top corner of screen and connect to the VPN.
If the GUI connection does not work, we can connect using 
```openvpn --config hackloab.ovpn```

12. Open a new terminal and check whether we are assigned an IP in the range 10.8.0.0/24 using the following commands

```ip a``` and ```ip route``` (to see that default gateway has changed)

13. Install additional tool for reconnaissance called metagoofil -
```
apt-get install metagoofil
```

14. Install additional tool from github, Sniper which is a ruby based point and click scanner/assessment tool -
```
cd /opt
git clone https://github.com/1N3/Sn1per
cd Sn1per
chmod +x install.sh
./install.sh
```

15. Not useful tools but optional-
```
sudo apt-get install figlet
``` 
This can be used to create logon banner by adding ```figlet -username-``` to the .bashrc script using ```vim ~/.bashrc```

```
sudo apt-get install sl fortune cowsay
```
Add this to default path by adding following lines to .bashrc file
```
PATH=$PATH:/usr/games
export PATH
```

and execute the following after doing ```source .bash_rc``` 
```
fortune | cowsaw -f flaming-sheep
```

16. To find files use the find command, 
```
find /usr -name "rockyou*"
```

Another method is the locate command, which uses an indexed database so we have to run ```updatedb``` regularly to update
```locate rockyou```

For executable files, we can use which and whereis commands , but their executables need to be in the PATH
```
which msfconsole
whereis nmap
```

17. Remember to use whatis and man to find out about a linux command










