# Installing WSL
### Step 1: Check if your Windows is up to date.
To do so press "windows-key + r" and type winver.
For x64 systems: Version 1903 or higher, with Build 18362 or higher.
For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
Builds lower than 18362 do not support WSL 2. Use the Windows Update Assistant to update your version of Windows.

### Step 2: Install WSL2
You can install WSL2 by following steps here: https://docs.microsoft.com/en-us/windows/wsl/install-win10

* Please only follow till step 5 in the link given above.
* The windows version number and build number will be useful in determining whether or not your system needs to be updated.

### Step 3: Installing the ubuntu app from the Microsoft Store.
Install Ubuntu 18.04 LTS from the Microsoft Store. NOTE: Using “Ubuntu” or "or Ubuntu 20.04" will NOT work properly. Only use Ubuntu 18.04.
Once it is installed, run the app from the startup menu. After initializing your environment, it will ask you to create a user. Provide a username and password.

### Step 4: Download and install google-chrome (in the Ubuntu Environment):

Run the following command to download latest chrome:
```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
```

Make sure to install chrome outside of any important directory.


# RDP_Client_Server

### Adding a lightweight desktop environment
```
sudo apt update && sudo apt -y upgrade  
sudo apt-get purge xrdp  
sudo apt install -y xrdp  
sudo apt install -y xfce4  
sudo apt install -y xfce4-goodies  
sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak  
sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini  
sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini  
sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini  
echo xfce4-session > ~/.xsession
```

### Edit Config
```
sudo nano /etc/xrdp/startwm.sh 
```

### Comment lines
```
#test -x /etc/X11/Xsession && exec /etc/X11/Xsession
#exec /bin/sh /etc/X11/Xsession
```


### Add lines
```
# xfce
startxfce4
```

### Start the rdp server
```
sudo /etc/init.d/xrdp start
```
