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
