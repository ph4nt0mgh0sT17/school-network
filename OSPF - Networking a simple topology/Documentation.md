<b>Propojení jednoduché sítě pomocí dynamického směrovacího protokolu OSPF</b>

Topologie skýtá 2 směrovače (routery) které jsou propojené skrz serial cable a mají každý z nich svou druhou síť propojenou Fast Ethernet cable.

Konfigurace prvního směrovače R1 (ten levý):
Router>enable
Router#configure terminal
Router(config)#interface s0/2/0
Router(config-if)#ip address 172.16.0.1 255.255.255.252
Router(config-if)#clock rate 128000
Router(config-if)#no shutdown
Router(config-if)#exit

Router(config)#inerfacet fa0/0
Router(config-if)#ip address 192.168.1.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit

Router(config)#router ospf 1
Router(config-router)#network 192.168.1.0 0.0.0.255 area 0
Router(config-router)#network 172.16.0.0 0.0.0.3 area 0
Router(config-router)#exit

Konfigurace druhého směrovače R2 (ten pravý):
Router>enable
Router#configure terminal
Router(config)#interface s0/0/0
Router(config-if)#ip address 172.16.0.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit

Router(config)#int fa0/0
Router(config-if)#ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)#exit

Router(config)#router ospf 1
Router(config-router)#network 192.168.2.0 0.0.0.255 area 0
Router(config-router)#network 172.16.0.0 0.0.0.3 area 0
Router(config-router)#exit
