## Azure Function Core Tools: Debian
Second, add the Azure Functions core tools so you can develop function apps locally.  
https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=linux%2Ccsharp%2Cbash

```posix
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
```
```posix
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/debian/$(lsb_release -rs | cut -d'.' -f 1)/prod $(lsb_release -cs) main" > /etc/apt/sources.list.d/dotnetdev.list'
```
If you like, you can check your Deb version is in the generated config list.  
```posix
/etc/apt/sources.list.d/dotnetdev.list
```
Then perform the core tools installation.  
```posix
sudo apt-get update
sudo apt-get install azure-functions-core-tools-4
```


### Debian Repository Version Issue  
Core tools 4 is missing from Deb 12 (as of Oct 2023).  Manually edit your dotnetdev.list file and change this enttry:  
```
deb [arch=amd64] https://packages.microsoft.com/debian/12/prod bookworm main
```
To this entry:  
```
deb [arch=amd64] https://packages.microsoft.com/debian/11/prod bullseye main
```
Then run the apt update and install, check you have the right version.  
```posix
func --version
```