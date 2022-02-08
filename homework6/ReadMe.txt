Router0:

Building configuration...

Current configuration : 957 bytes
!
version 12.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
ip dhcp pool pool.192.168.1.0
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8
!
!
!
ip cef
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
duplex auto
speed auto
!
interface FastEthernet1/0
no ip address
duplex auto
speed auto
shutdown
!
interface Serial2/0
no ip address
clock rate 2000000
shutdown
!
interface Serial3/0
no ip address
clock rate 2000000
shutdown
!
interface FastEthernet4/0
ip address 172.17.0.1 255.255.0.0
!
interface FastEthernet5/0
ip address 172.16.0.1 255.255.0.0
!
router rip
version 2
network 172.16.0.0
network 172.17.0.0
network 192.168.1.0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
login
!
!
!
end

Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
* - candidate default, U - per-user static route, o - ODR
P - periodic downloaded static route

Gateway of last resort is not set

C 172.16.0.0/16 is directly connected, FastEthernet5/0
C 172.17.0.0/16 is directly connected, FastEthernet4/0
R 172.18.0.0/16 [120/1] via 172.17.0.2, 00:00:17, FastEthernet4/0
[120/1] via 172.16.0.2, 00:00:20, FastEthernet5/0
C 192.168.1.0/24 is directly connected, FastEthernet0/0
R 192.168.2.0/24 [120/1] via 172.17.0.2, 00:00:17, FastEthernet4/0
R 192.168.3.0/24 [120/1] via 172.16.0.2, 00:00:20, FastEthernet5/0

Router1:

Building configuration...

Current configuration : 957 bytes
!
version 12.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
ip dhcp pool pool.192.168.2.0
network 192.168.2.0 255.255.255.0
default-router 192.168.2.1
dns-server 8.8.8.8
!
!
!
ip cef
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
ip address 192.168.2.1 255.255.255.0
duplex auto
speed auto
!
interface FastEthernet1/0
no ip address
duplex auto
speed auto
shutdown
!
interface Serial2/0
no ip address
clock rate 2000000
shutdown
!
interface Serial3/0
no ip address
clock rate 2000000
shutdown
!
interface FastEthernet4/0
ip address 172.17.0.2 255.255.0.0
!
interface FastEthernet5/0
ip address 172.18.0.1 255.255.0.0
!
router rip
version 2
network 172.17.0.0
network 172.18.0.0
network 192.168.2.0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
login
!
!
!
end

Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
* - candidate default, U - per-user static route, o - ODR
P - periodic downloaded static route

Gateway of last resort is not set

R 172.16.0.0/16 [120/1] via 172.18.0.2, 00:00:16, FastEthernet5/0
[120/1] via 172.17.0.1, 00:00:06, FastEthernet4/0
C 172.17.0.0/16 is directly connected, FastEthernet4/0
C 172.18.0.0/16 is directly connected, FastEthernet5/0
R 192.168.1.0/24 [120/1] via 172.17.0.1, 00:00:06, FastEthernet4/0
C 192.168.2.0/24 is directly connected, FastEthernet0/0
R 192.168.3.0/24 [120/1] via 172.18.0.2, 00:00:16, FastEthernet5/0

Router2:

Building configuration...

Current configuration : 957 bytes
!
version 12.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Router
!
!
!
!
!
ip dhcp pool pool.192.168.3.0
network 192.168.3.0 255.255.255.0
default-router 192.168.3.1
dns-server 8.8.8.8
!
!
!
ip cef
no ipv6 cef
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface FastEthernet0/0
ip address 192.168.3.1 255.255.255.0
duplex auto
speed auto
!
interface FastEthernet1/0
no ip address
duplex auto
speed auto
shutdown
!
interface Serial2/0
no ip address
clock rate 2000000
shutdown
!
interface Serial3/0
no ip address
clock rate 2000000
shutdown
!
interface FastEthernet4/0
ip address 172.18.0.2 255.255.0.0
!
interface FastEthernet5/0
ip address 172.16.0.2 255.255.0.0
!
router rip
version 2
network 172.16.0.0
network 172.18.0.0
network 192.168.3.0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
login
!
!
!
end

Codes: C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP
D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
* - candidate default, U - per-user static route, o - ODR
P - periodic downloaded static route

Gateway of last resort is not set

C 172.16.0.0/16 is directly connected, FastEthernet5/0
R 172.17.0.0/16 [120/1] via 172.18.0.1, 00:00:20, FastEthernet4/0
[120/1] via 172.16.0.1, 00:00:16, FastEthernet5/0
C 172.18.0.0/16 is directly connected, FastEthernet4/0
R 192.168.1.0/24 [120/1] via 172.16.0.1, 00:00:16, FastEthernet5/0
R 192.168.2.0/24 [120/1] via 172.18.0.1, 00:00:20, FastEthernet4/0
C 192.168.3.0/24 is directly connected, FastEthernet0/0

По командам: no ip (удалим статику)
route rip
version 2
(Включили протокол)
network 19.168.1.0 (для примера) включили маршрут на сеть
по dhcp все из методички.