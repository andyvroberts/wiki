
## SSH Keygen
This sample is for linux environments only and assume you have openssh-client installed.  
Generat a public/private key pair. 
```
ssh-keygen
```
The default key files are id_rsa (private key) and id_rsa.pub (public key).  If you need to generate a second pair, the files names should be different.   
For example, I tend to use id_rsa for github and id_rsa_ado for azure devops.  

## Git Configuration
Create some required global settings.
```
git config --global init.defaultBranch main
git config --global user.name "name"
git config --global user.email "name@email"
```
