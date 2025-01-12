## Python : Tools

### Jupyter
Install a Jupyter kernel for the VS Code Jupyter extension.
```
pip install ipython ipykernel
```
If you installed this in a .venv then the python environment is the same as the Jupyter server location.  

To add an api key in a VS Code notebooke use this: 
```
import getpass
api_key = getpass.getpass("enter the api key")
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
