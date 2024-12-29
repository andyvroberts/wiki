## Alpine WSL
Add [virtualenv](https://virtualenv.pypa.io/en/latest/user_guide.html) to Alpine as python3-venv does not exist. 
```
doas apk add py3-virtualenv
```
Add an environment and activate it.  
```
virtualenv .venv
source .venv/bin/activate
```

