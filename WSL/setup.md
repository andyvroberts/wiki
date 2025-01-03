## WSL
Windows Sub-system for Linux allows you to create linux environments on Windows.  [Read the docs](https://learn.microsoft.com/en-us/windows/wsl/about).  

### Install WSL 2
It used to be weird, now it's easy using an Admin PS prompt:  
```ps
wsl --install
```
By default, this installs Ubuntu but you can switch it to another flavour with the install command options.  Other Linux environments are:  
```ps
wsl --list --online
```
which can result in:  
```ps
wsl --install -d Debian
```
---

### General Commands
What are my installed WSL Linux environments:  
```ps
wsl --list --verbose
```

Update WSL, check the status, shutdown, terminate an executing environment:  
```ps 
wsl --update
wsl --status
wsl --shutdown
wsl --terminate Debian
```

Performing an uninstall of a WSL environment does not delete its files.  To remove them run this uninstall command for the distribution:  
```ps
wsl --unregister Debian
```

What is my WSL Linux IP address:  
```ps
wsl hostname -I
```

From Linux, what is the host Windows IP address:  
```bash
ip route show | grep -i default | awk '{ print $3}'
```

Putting you computer to sleep has clock synchronisation problems when connecting to Azure using the Linux AZ CLI. To recover from this within yoru WSL environment run:  
```bash
sudo hwclock -s
```
---

### Duplicate an New WSL Environment
If you require multiple environments (several Debian 12's, etc.), you cannot install these from the windows store or using the [*wsl --install*] command.  But you can re-create them again from a base image already downloaded.  

First, locate your existing Debian install.tar.gz file.  This is usually found in your WindowsApps folder.  These following commands that access the C drive are run in a powershell Admin prompt.  
```ps
cd "C:\Program Files\WindowsApps"
dir TheDebianProject*

>>Mode          LastWriteTime         Length    Name
>> ----         -------------         ------    ----
>>d----         30/12/2024 10:53                TheDebianProject.DebianGNULinux_1.18.0.0_x64__76v4gfsz19hv4

cd TheDebianProject.DebianGNULinux_1.18.0.0_x64__76v4gfsz19hv4
dir install*

>>Mode      LastWriteTime        Length     Name
>>----      -------------        ------     ----
>>-a---     30/12/2024 10:53     97511802   install.tar.gz
```

Or, if you know some powershell commands this is especially useful if you have multiple Linux versions already installed:  
```ps
 Get-ChildItem -Recurse 'C:\Program Files\WindowsApps\' | Where-Object {$_.Name -eq 'install.tar.gz' }

>>    Directory: C:\Program Files\WindowsApps\TheDebianProject.DebianGNULinux_1.18.0.0_x64__76v4gfsz19hv4

>>Mode      LastWriteTime       Length      Name
>>----      -------------       ------      ----
>>-a---     30/12/2024 10:53    97511802    install.tar.gz
```

When you create a duplicate environment, you can put the resulting vhdx file anywhere you please.  By default, these are placed in the uisers AppData folder.  
```ps
cd %HOME
>> C:\Users\avrob>

cd AppData\Local\Packages
ls TheDebianProject*
>>Mode      LastWriteTime         Length    Name
>> ----     -------------         ------    ----
>>d----     13/07/2024 10:36                TheDebianProject.DebianGNULinux_76v4gfsz19hv4
```
#### Run the Duplication:
Just create a directory location and run the install to create it in that folder destination.  
Note, this does not require an admin elevation.  
```ps
mkdir -p WSL/instances/debian-spark
wsl --import debian-spark C:\WSL\instances\debian-spark "C:\Program Files\WindowsApps\TheDebianProject.DebianGNULinux_1.18.0.0_x64__76v4gfsz19hv4\install.tar.gz"
```
The vhdx file will now exist in that location and if you have already configured Windows Terminal, it should automatically show in the list.

```ps
cd \wsl\instances\debian-spark
ls

>>Mode      LastWriteTime       Length      Name
>>----      -------------       ------      ----
>>-a----    01/01/2025 10:33    370147328   ext4.vhdx
```

#### Startup User
To make this a user the default one on startup, edit the wsl.conf file.  
```bash
vi /etc/wsl.conf

[user]
default=avrob
:wq
```
To open a new session in that users home directory, edit the WSL conf JSON file:
```json
            {
                "guid": "{13873086-2643-5f53-88ea-c95295a85640}",
                "hidden": false,
                "name": "Alpine321",
                "source": "Windows.Terminal.Wsl",
                "startingDirectory": "\\\\wsl$\\Alpine321\\home\\avrob"
            }
```
