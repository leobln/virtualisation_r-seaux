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

