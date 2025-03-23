
## SSH Keygen
This sample is for linux environments only and assumes you have openssh-client installed.  
Generate a public/private key pair. 
```
ssh-keygen
ssh-keygen -t rsa -b 4096 -f ~/.ssh/ado_rsa
```
The default key files are id_rsa (private key) and id_rsa.pub (public key). They are put in your [_home/.ssh]_ directory but of course you can place them anywhere you like.  If you need to generate a second pair, the files names should be different.   
  
For example, I tend to use id_rsa for github and any other file name for azure devops.  

To set a particular key in your current environment without having to be prompoted on every remote push or pull (or to avoid password requests from the git credential manager) do this:  
```
eval $(ssh-agent)
ssh_add ~/.ssh/id_rsa
```

## Git Configuration
Create some required global settings.
```
git config --global init.defaultBranch main
git config --global user.name "name"
git config --global user.email "name@email"
```
