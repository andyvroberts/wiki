## Python: Alpine WSL
Add [virtualenv](https://virtualenv.pypa.io/en/latest/user_guide.html) to Alpine as python3-venv does not exist. 
```
doas apk add py3-virtualenv
```
Add an environment and activate it.  
```
virtualenv .venv
source .venv/bin/activate
```

## Python: Debian WSL
If you are developing Azure Functions then also ensure it is compatible with Function Apps.  
Add the basic linux tools such as gcc, open-ssh (within git), etc.  
```posix
sudo apt-get install wget
sudo apt-get install curl
sudo apt-get install git
sudo apt-get install build-essential
```

Download a python tgz file and install as the default in debian, which is located in the */usr/local/lib/pythonx.xx* folder but which runs from the */usr/local/bin* location.    
```posix
tar -xvf <python-file>.tgz
cd python-x.x.x
./configure --enable-optimizations
sudo make
sudo make install
```
If you want to add a another python version then make it as an alternative install which puts it into the users home folder path.  
```posix
sudo make altinstall
```

Finish adding other python installs.  
```posix
sudo apt-get install python3-venv
sudo apt-get install python3-pip
```
