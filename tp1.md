🌞 Déterminer l'adresse MAC de vos deux machines

    depuis le terminal de chacun des clients (VM Rocky ou VPCS), déterminer son adresse MAC
    une seule commande est nécessaire sur chaque client

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
