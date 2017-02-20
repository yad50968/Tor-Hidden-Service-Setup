# Tor-Hidden-Service-Setup

### Environment
OS : MacOSX Sierra 10.12.2 <br>
Apache : 2.4.23

### Step
#### Install MacPort
```
  Download the MacPort.pkg
  From https://github.com/macports/macports-base/releases/download/v2.4.0/MacPorts-2.4.0-10.12-Sierra.pkg
  
  Install , it may install under /opt/local/bin/
```

#### Install tor
```
  sudo port install tor
```

#### Make a directory, use to store sk, onion url
```
  cd /Users/{Your-home-name}
  mkdir hidden-service
  shdo chmod 700 hidden-service  # You can't give the folder too permissive
```
#### Modify the torrc

  After install tor <br>
  /usr/local/ect/tor/ has torrc.sample <br>
  Modify it!
```
  sudo cp torrc.sample torrc
  sudo vim torrc
```
  Insert the following to torrc
```
  SocksPort 9050 # You have to open this port! See reference 3
  SockListenAddress 127.0.0.1
  HiddenServiceDir /Users/{Your-home-name}/hidden-service/  # Absolute path
  HiddenServicePort 80 127.0.0.1:80   # first port : for tor,  second port : for your server
```
#### Run tor
``` 
  Use console, run tor
  
  It will generate the private key file and onion url file
  in the hidden-service/
```
#### Run Apache
```
  sudo apacthe start
```

#### Open tor browser
```
  Connect to the onion url in the hidden-service/hostname/
```

### Reference
1. https://www.torproject.org/docs/tor-hidden-service.html.en
2. https://github.com/whackashoe/tor-hidden-service-setup/blob/master/setting-up-webserver.md
3. https://rolfje.wordpress.com/2014/05/10/open-a-port-in-osx-mavericks-firewall/
