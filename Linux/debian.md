## Linux: Debian WSL

### Add A User
With an emtpy environment (check you are root) first create a new user.  
```bash
whoami
adduser avrob
```
This creates a user and the home folder in /home/avrob, and populates it with default files from etc/skel.  
On Debian, this command also puts the user into the /etc/passwd file and sets the default shell to bash.  

Add the new user to the Sudo group so it can run elevated operations.  
```bash
sudo usermod -aG sudo avrob
```

Finally, make this user the default one on startup by editing the wsl.conf file.  
```bash
vi /etc/wsl.conf

[user]
default=avrob
:wq
```

To Delete a user and remove the home folder, su (switch user) to root and run:  
```bash
deluser avrob --remove-home
```

Add basic packages
```
sudo apt update
sudo apt upgrade
sudo apt-get install wget
sudo apt-get install git
sudo apt install openssh-client
```

