# dnstumbler
A DNS randomizer, that can operate in listener or sender mode. Just a random project to see if your network sensors pick up on completely bogus DNS traffic that is abornmal. To get responses with bogus info, operate two instances (one sender and one listener)

## Dependencies
  `pip install scapy`

## Typical Usage
  ### Sender
    sudo python3 dnstumbler.py -d <upstream DNS server> -a '<apexdomain>'

    sudo python3 dnstumbler.py -d 1.1.1.1 -a 'example.com'

  ### Listener
    sudo python3 dnstumbler.py --listener -a '<apexdomain>' -i '<interface>'

    sudo python3 dnstumbler.py --listener -a 'example.com' -i 'ens33'
  
  ### Help
  python3 dnstumbler.py -h
  


#### Random note

  The native TCP/IP stack will interfere with traffic from scapy because of "unsolicited" DNS requests. Block output "ICMP unreachable" messages with IPTABLES.
  
    `sudo iptables -A OUTPUT -p ICMP --icmp-type port-unreachable -j DROP`
