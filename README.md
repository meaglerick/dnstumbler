# dnstumbler
A DNS randomizer, that can operate in listener or sender mode. Just a random project to see if your network sensors pick up on completely bogus DNS traffic that is abornmal. To get responses with bogus info, operate two instances (one sender and one listener)

## Dependencies
  `pip install scapy`

## Typical Usage
  ### Sender
    `sudo python3 dnstumbler.py -d <upstream DNS server> -a '<apexdomain>'`

    `sudo python3 dnstumbler.py -d 1.1.1.1 -a 'example.com'

  ### Listener
    `sudo python3 dnstumbler.py --listener -a '<apexdomain>' -i '<interface>'`

    `sudo python3 dnstumbler.py --listener -a 'example.com' -i 'ens33'`
  
  ### Help
  python3 dnstumbler.py -h
  


#### Random note

  If you're running this on debian/ubuntu that runs systemd-resolv...disable it. Otherwise it just interferes with the normal DNS traffic.
  How to disable systemd-resolved in Ubuntu

  Disable and stop the systemd-resolved service:

    sudo systemctl disable systemd-resolved.service
    sudo systemctl stop systemd-resolved

  Then put the following line in the [main] section of your /etc/NetworkManager/NetworkManager.conf:

    dns=default
  Delete the symlink /etc/resolv.conf

    rm /etc/resolv.conf
  Restart network-manager

    sudo service network-manager restart
  https://gist.github.com/zoilomora/f7d264cefbb589f3f1b1fc2cea2c844c
