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

📁 [p1_ping](./fichier_wiresshark/p1_ping.pcapng)

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

📁 [p2_arp_node2 ](./fichier_wiresshark/p2_arp_node2.pcapng)

📁 [p2_arp_node3 ](./fichier_wiresshark/p2_arp_node3.pcapng)

## Partie 3

🌞 Installer un serveur DHCP

```
[leobln@efrei-xmg4agau1 ~]$ dnf install dnsmasq
[...]
[leobln@efrei-xmg4agau1 ~]$ vi /etc/dnsmasq.conf
"ligne 183"dhcp-range=10.1.1.10,10.1.1.50,12h

# pour node 1
VPCS> ip dhcp
DDORA IP 10.1.1.47/24 GW 10.1.1.253

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.47/24         10.1.1.253        00:50:79:66:68:02  10004  127.0.0.1:10005
       fe80::250:79ff:fe66:6802/64

# pour node2

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.2/24          0.0.0.0           00:50:79:66:68:01  10006  127.0.0.1:10007
       fe80::250:79ff:fe66:6801/64

VPCS> ip dhcp
DDORA IP 10.1.1.46/24 GW 10.1.1.253

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.46/24         10.1.1.253        00:50:79:66:68:01  10006  127.0.0.1:10007
       fe80::250:79ff:fe66:6801/64

# pour node 3

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.3/24          0.0.0.0           00:50:79:66:68:00  10008  127.0.0.1:10009
       fe80::250:79ff:fe66:6800/64

VPCS> ip dhcp
DDORA IP 10.1.1.45/24 GW 10.1.1.253

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.45/24         10.1.1.253        00:50:79:66:68:00  10008  127.0.0.1:10009
       fe80::250:79ff:fe66:6800/64
``` 
📁 [p3_dhcp](./fichier_wiresshark/p3_dhcp.pcapng)

🌞 Bail DHCP

🌞 Use grep

```
[leobln@efrei-xmg4agau1 ~]$ sudo cat /var/lib/dnsmasq/dnsmasq.leases
[sudo] Mot de passe de leobln :
1767747471 00:50:79:66:68:00 10.1.1.45 * 01:00:50:79:66:68:00
1767747390 00:50:79:66:68:01 10.1.1.46 * 01:00:50:79:66:68:01
1767747914 00:50:79:66:68:02 10.1.1.47 VPCS1 01:00:50:79:66:68:02

# sachant que l'adresse mac de node 1 est : 00:50:79:66:68:02
donc il correspond a la troisieme ligne 

[leobln@efrei-xmg4agau1 ~]$ sudo cat /var/lib/dnsmasq/dnsmasq.leases | grep 00:50:79:66:68:02
[sudo] Mot de passe de leobln :
1767747914 00:50:79:66:68:02 10.1.1.47 VPCS1 01:00:50:79:66:68:02
```

## Partie 4

🌞 Installez et configurez un serveur DHCP

🌞 Test !

```
# pour node1

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.47/24         10.1.1.253        00:50:79:66:68:02  10004  127.0.0.1:10005
       fe80::250:79ff:fe66:6802/64

VPCS> ip dhcp
DORA IP 10.1.1.247/24 GW 10.1.1.31

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.247/24        10.1.1.31         00:50:79:66:68:02  10004  127.0.0.1:10005
       fe80::250:79ff:fe66:6802/64

# pour node2

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.46/24         10.1.1.253        00:50:79:66:68:01  10006  127.0.0.1:10007
       fe80::250:79ff:fe66:6801/64

VPCS> ip dhcp
DDORA IP 10.1.1.246/24 GW 10.1.1.31

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.246/24        10.1.1.31         00:50:79:66:68:01  10006  127.0.0.1:10007
       fe80::250:79ff:fe66:6801/64

# pour node3

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.45/24         10.1.1.253        00:50:79:66:68:00  10008  127.0.0.1:10009
       fe80::250:79ff:fe66:6800/64

VPCS> ip dhcp
DDORA IP 10.1.1.245/24 GW 10.1.1.31

VPCS> show

NAME   IP/MASK              GATEWAY           MAC                LPORT  RHOST:PORT
VPCS1  10.1.1.245/24        10.1.1.31         00:50:79:66:68:00  10008  127.0.0.1:10009
       fe80::250:79ff:fe66:6800/64


```

📁 [p4_dhcp_race](./fichier_wiresshark/p4_dhcp_race.pcapng)

🌞 ARP poisoning

```
#commande utiliser

sudo arping -c 1 -U -s 10.1.1.100 -I enp0s8 10.1.1.247

# vision de node1

VPCS> arp

08:00:27:99:83:4b  10.1.1.100 expires in 111 seconds
```

📁 [p4_poisoning](./fichier_wiresshark/p4_poisoning.pcapng)

🌞 MITM

```
#commande utiliser sur node1

sudo arping -c 1 -U -s 10.1.1.246 -I enp0s8 10.1.1.247

#commande utiliser sur node2

sudo arping -c 1 -U -s 10.1.1.247 -I enp0s8 10.1.1.246
```

📁 [p4_mitm.pcap](./fichier_wiresshark/p4_mitm.pcapng)

