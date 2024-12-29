## Alpine WSL
Find the latest supported sdk version and add it.  
```
doas apk add dotnet8-sdk
```

If it does not install, you may need to search the [Alpine releases](https://pkgs.alpinelinux.org/packages?name=dotnet*&branch=v3.17&repo=&arch=x86_64&origin=&flagged=&maintainer=) for the available dotnet versions of the etc/apk/repositories main and community repos. 
   
For example, if WSL Alpine is 3.17, that means you can only install up to SDK 7.0    
```
doas apk add dotnet7-sdk
```



