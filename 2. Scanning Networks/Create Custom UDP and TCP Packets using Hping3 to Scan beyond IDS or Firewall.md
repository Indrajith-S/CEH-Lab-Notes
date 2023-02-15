- Using hping3
>hping3 #ip --udp --rand-source --data 500 

- Here, **--udp** specifies sending the UDP packets to the target host, **--rand-source** enables the random source mode and **--data** specifies the packet body size.

	> hping3 -S #ip -p 80 -c 5
	
- Here, **-S** specifies the TCP SYN request on the target machine, **-p** specifies assigning the port to send the traffic, and **-c** is the count of the packets sent to the target machine.

	> hping3 #ip --flood

- **--flood**: performs the TCP flooding.
