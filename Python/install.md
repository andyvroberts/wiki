## Python: Alpine WSL
Check the Alpine Package Index for the Alpine version you have installed.  For example, [Alpine 3.21 packages can be found here](https://pkgs.alpinelinux.org/packages?name=python*&branch=v3.21&repo=&arch=x86_64&origin=&flagged=&maintainer=).  
```bash
doas apk add python3
```

Add [virtualenv](https://virtualenv.pypa.io/en/latest/user_guide.html) to Alpine. 
```
doas apk add py3-virtualenv
```
Add an environment and activate it.  
```
virtualenv .venv
source .venv/bin/activate
```

## Python: Debian WSL
### Aptitude
Update the repo then install Python3 and its tools.  
```bash
sudo apt update
sudo apt install python3
sudo apt install python3-pop
sudo apt install python3-venv
```

### Manually
If you are developing Azure Functions then also ensure it is compatible with Function Apps.  
Add the basic linux tools such as gcc, open-ssh (within git), etc.  
```bash
sudo apt-get install wget
sudo apt-get install curl
sudo apt-get install git
sudo apt-get install build-essential
```

And for additional packages needed for Python Make:
```bash
sudo apt install zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libbz2-dev
sudo apt install libsqlite3-0 media-types openssl libexpat1 libnsl2 ca-certificates
```

Download a python tgz file and install as the default in debian, which is located in the */usr/local/lib/pythonx.xx* folder but which runs from the */usr/local/bin* location.    
```bash
wget -q https://www.python.org/ftp/python/3.12.8/Python-3.12.8.tar.xz

tar -xvf Python-3.12.8.tar.xz.xz
cd python-3.12.8
./configure --enable-optimizations
sudo make
sudo make install
```
If you want to add a another python version then make it as an alternative install which puts it into the users home folder path.  
```bash
sudo make altinstall
```

Finish adding other python installs.  
```bash
sudo apt-get install python3-venv
sudo apt-get install python3-pip
```
