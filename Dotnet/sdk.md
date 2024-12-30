## Dotnet: Alpine WSL
Find the latest supported sdk version and add it.  
```
doas apk add dotnet8-sdk
```

If it does not install, you may need to search the [Alpine releases](https://pkgs.alpinelinux.org/packages?name=dotnet*&branch=v3.17&repo=&arch=x86_64&origin=&flagged=&maintainer=) for the available dotnet versions of the etc/apk/repositories main and community repos. 
   
For example, if WSL Alpine is 3.17, that means you can only install up to SDK 7.0    
```
doas apk add dotnet7-sdk
```

## Dotnet: Debian
Always read the latest docs:  
https://docs.microsoft.com/en-us/dotnet/core/install/linux  

What is your Deb version?  
```posix
cat /etc/os-release
```

Run the installation process using apt (this code snippet is copied from the microsft docs pages):  
```posix
wget https://packages.microsoft.com/config/debian/12/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
```
```posix
sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-7.0
```
Check you have what you expect.  
```posix
dotnet --list-sdks
```

