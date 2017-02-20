# Tor-Hidden-Service-Setup

### Environment
OS : MacOSX Sierra 10.12.2 <br>
Apache : 2.4.23

### Step
##### Install MacPort
```
  Download the [MacPort.pkg](https://github.com/macports/macports-base/releases/download/v2.4.0/MacPorts-2.4.0-10.12-Sierra.pkg)
  Install , it may install under /opt/local/bin/
```
##### Install tor
```
  sudo port install tor
```

##### Make a directory, use to store some information
```
  cd /Users/{Your-home-name}
  mkdir hidden-service
  shdo chmod 700 hidden-service  # You can't give the folder too permissive
```
##### Modify the torrc

  After you install tor, /usr/local/ect/tor/ has torrc.sample
```
  sudo cp torrc.sample torrc
  sudo vim torrc
```
  Insert the following
```
  SocksPort 9050 # You have to open this port! See reference 3
  SockListenAddress 127.0.0.1
  HiddenServiceDir /Users/{Your-home-name}/hidden-service/  # Absolute path
  HiddenServicePort 80 127.0.0.1:80   # first port : for tor,  second port : for your server
```
##### Run tor
``` 
  Use console, run tor
```
##### Run Apache
```
  sudo apacthe start
```

##### Open tor browser
```
  Connect to the url under the hidden-service/
```

### Reference
1. https://www.torproject.org/docs/tor-hidden-service.html.en
2. https://github.com/whackashoe/tor-hidden-service-setup/blob/master/setting-up-webserver.md
3. https://rolfje.wordpress.com/2014/05/10/open-a-port-in-osx-mavericks-firewall/
