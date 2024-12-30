## Azure CLI: Debian
First add the CLI.  Check the docs again, to ensure your Deb version is compatible.  
https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt  

Use their single bash install script.  
```posix
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```
Also, check you have what you expect.  
```posix
az --version
```