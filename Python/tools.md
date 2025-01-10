## Python : Tools

### SSH Keygen
Generat a public/private key pair. 
```
ssh-keygen
```

### Git Configuration
Create some required global settings.
```
git config --global init.defaultBranch main
git config --global user.name "name"
git config --global user.email "name@email"
```

### Parquet
To read parquet formatted files via the command line, install the cli.
```
sudo apt-get install parquet-tools
```

Then view parquet files easily.
```
parq PostcodeToLA.parquet --head 10
```
