## Partie 1
🌞 Déterminer l'adresse MAC de vos deux machines
    
🌞 Définir une IP statique sur les deux machines

🌞 Proof !

🌞 Effectuer un ping d'une machine à l'autre

```
# pour node1.tp1.efrei

PC1> ip 10.1.1.1
Checking for duplicate address...
PC1 : 10.1.1.1 255.255.255.0

PC1> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
PC1    10.1.1.1/24          0.0.0.0           00:50:79:66:68:00  10004  127.0.0.1:10005
       fe80::250:79ff:fe66:6800/64

PC1> ping 10.1.1.2
84 bytes from 10.1.1.2 icmp_seq=1 ttl=64 time=0.536 ms
84 bytes from 10.1.1.2 icmp_seq=2 ttl=64 time=0.726 ms

# pour node2.tp1.efrei

PC2> ip 10.1.1.2
Checking for duplicate address...
PC1 : 10.1.1.2 255.255.255.0

PC2> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PO      RT
PC2    10.1.1.2/24          0.0.0.0           00:50:79:66:68:01  10002  127.0.0.      1:10003
       fe80::250:79ff:fe66:6801/64

PC2> ping 10.1.1.1
84 bytes from 10.1.1.1 icmp_seq=1 ttl=64 time=0.671 ms
84 bytes from 10.1.1.1 icmp_seq=2 ttl=64 time=0.898 ms
```
🌞 Protocolz ?

📁 [p1_ping.pcap](./p1_ping.pcapng)

## Partie 2

🌞 Déterminer l'adresse MAC de vos trois machines

🌞 Définir une IP statique sur les trois machines

🌞 Effectuer des ping d'une machine à l'autre

```
# pour node1(voir p1 pour ip+show)

VPCS> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=7.606 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=3.740 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=3.186 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=4.829 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=3.746 ms

# pour node2(voir p1 pour ip+show)

VPCS> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=3.308 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=3.343 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=2.371 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=2.482 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=2.285 ms


# pour node3

VPCS> ip 10.1.1.3
Checking for duplicate address...
PC1 : 10.1.1.3 255.255.255.0

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.3/24          0.0.0.0           00:50:79:66:68:02  10000  127.0.0.1:10001
       fe80::250:79ff:fe66:6802/64

VPCS> ping 10.1.1.1
84 bytes from 10.1.1.1 icmp_seq=1 ttl=64 time=5.306 ms
84 bytes from 10.1.1.1 icmp_seq=2 ttl=64 time=3.252 ms
84 bytes from 10.1.1.1 icmp_seq=3 ttl=64 time=3.020 ms
84 bytes from 10.1.1.1 icmp_seq=4 ttl=64 time=2.243 ms
84 bytes from 10.1.1.1 icmp_seq=5 ttl=64 time=1.980 ms

VPCS> ping 10.1.1.2
84 bytes from 10.1.1.2 icmp_seq=1 ttl=64 time=2.795 ms
84 bytes from 10.1.1.2 icmp_seq=2 ttl=64 time=3.528 ms
84 bytes from 10.1.1.2 icmp_seq=3 ttl=64 time=3.434 ms
84 bytes from 10.1.1.2 icmp_seq=4 ttl=64 time=1.946 ms
84 bytes from 10.1.1.2 icmp_seq=5 ttl=64 time=3.717 ms
```

🌞 Afficher la table ARP de node1

```
VPCS> arp

00:50:79:66:68:01  10.1.1.2 expires in 105 seconds
00:50:79:66:68:02  10.1.1.3 expires in 113 seconds
```

📁 [p2_arp_node2.pcap ](./p2_arp_node2.pcapng)

📁 [p2_arp_node3.pcap ](./p2_arp_node3.pcapng)