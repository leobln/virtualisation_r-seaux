🌞 Tout le monde doit pouvoir se ping

```
# pour node1

VPCS> ping 10.2.1.12

84 bytes from 10.2.1.12 icmp_seq=1 ttl=64 time=8.971 ms
84 bytes from 10.2.1.12 icmp_seq=2 ttl=64 time=6.835 ms
84 bytes from 10.2.1.12 icmp_seq=3 ttl=64 time=6.332 ms
84 bytes from 10.2.1.12 icmp_seq=4 ttl=64 time=7.073 ms
84 bytes from 10.2.1.12 icmp_seq=5 ttl=64 time=7.310 ms

# bref c'est  pareil pour les autres
```

📁 [p1_routed_ping](./fichier_wiresshark/p1_routed_ping.pcapng)

## Partie 2

🌞 Prouver que...

```
# pour R1

R1#ping 8.8.8.8

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 8.8.8.8, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 12/32/48 ms

# pour node1

VPCS> ping 8.8.8.8

8.8.8.8 icmp_seq=1 timeout
8.8.8.8 icmp_seq=2 timeout
8.8.8.8 icmp_seq=3 timeout
8.8.8.8 icmp_seq=4 timeout
8.8.8.8 icmp_seq=5 timeout
```

📁 [p2_no_nat](./fichier_wiresshark/p2_no_nat.pcapng)

🌞 Proooooooooof or lie

```
# pour node1

VPCS> ping 1.1.1.1

84 bytes from 1.1.1.1 icmp_seq=1 ttl=253 time=52.451 ms
84 bytes from 1.1.1.1 icmp_seq=2 ttl=253 time=52.140 ms
84 bytes from 1.1.1.1 icmp_seq=3 ttl=253 time=47.208 ms
84 bytes from 1.1.1.1 icmp_seq=4 ttl=253 time=46.824 ms
84 bytes from 1.1.1.1 icmp_seq=5 ttl=253 time=48.582 ms
```

📁 [p2_nat.pcap](./fichier_wiresshark/p2_nat.pcapng)

🌞 Prove it

```
VPCS> ping efrei.fr
efrei.fr resolved to 51.210.229.203

84 bytes from 51.210.229.203 icmp_seq=1 ttl=253 time=71.775 ms
84 bytes from 51.210.229.203 icmp_seq=2 ttl=253 time=48.913 ms
84 bytes from 51.210.229.203 icmp_seq=3 ttl=253 time=53.843 ms
84 bytes from 51.210.229.203 icmp_seq=4 ttl=253 time=52.359 ms
84 bytes from 51.210.229.203 icmp_seq=5 ttl=253 time=49.335 ms
```

🌞 Test test test

```
# pour node5

VPCS> show ip

NAME        : VPCS[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:04
LPORT       : 20031
RHOST:PORT  : 127.0.0.1:20032
MTU         : 1500

VPCS> ip dhcp
DDORA IP 10.2.1.164/24 GW 10.2.1.254

VPCS> ping efrei.fr
efrei.fr resolved to 51.210.229.203

84 bytes from 51.210.229.203 icmp_seq=1 ttl=253 time=44.269 ms
84 bytes from 51.210.229.203 icmp_seq=2 ttl=253 time=43.344 ms
84 bytes from 51.210.229.203 icmp_seq=3 ttl=253 time=46.965 ms
84 bytes from 51.210.229.203 icmp_seq=4 ttl=253 time=94.512 ms
84 bytes from 51.210.229.203 icmp_seq=5 ttl=253 time=42.038 ms

VPCS> show ip

NAME        : VPCS[1]
IP/MASK     : 10.2.1.164/24
GATEWAY     : 10.2.1.254
DNS         : 1.1.1.1
DHCP SERVER : 10.2.1.253
DHCP LEASE  : 43178, 43200/21600/37800
MAC         : 00:50:79:66:68:04
LPORT       : 20031
RHOST:PORT  : 127.0.0.1:20032
MTU         : 1500

```







