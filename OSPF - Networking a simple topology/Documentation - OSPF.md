<h1><b>OSPF - Vytvoření jednoduché sítě pomocí OSPF protokolu</b></h1>
<p>Topologie skýtá 2 směrovače ve své topologii a každý z nich má 2 sítě: Jednu společnou (serial cable) a jednu vlastní (Fast Ethernet Cable)</p>

<h2>Konfigurace směrovače R1 (ten levý)</h2>
<p>Router>enable</p>
<p>Router#configure terminal</p>
<p>Router(config)#interface s0/2/0</p>
<p>Router(config-if)#ip address 172.16.0.1 255.255.255.252</p>
<p>Router(config-if)#clock rate 128000</p>
<p>Router(config-if)#no shutdown</p>
<p>Router(config-if)#exit</p>
<br />
<p>Router(config)#inerface fa0/0</p>
<p>Router(config-if)#ip address 192.168.1.1 255.255.255.0</p>
<p>Router(config-if)#no shutdown</p>
<p>Router(config-if)#exit</p>
<br />
<p>Router(config)#router ospf 1</p>
<p>Router(config-router)#network 192.168.1.0 0.0.0.255 area 0</p>
<p>Router(config-router)#network 172.16.0.0 0.0.0.3 area 0</p>
<p>Router(config-router)#exit</p>
<br />
<h2>Konfigurace směrovače R1 (ten levý)</h2>
<p>Router>enable</p>
<p>Router#configure terminal</p>
<p>Router(config)#interface s0/0/0</p>
<p>Router(config-if)#ip address 172.16.0.2 255.255.255.252</p>
<p>Router(config-if)#no shutdown</p>
<p>Router(config-if)#exit</p>
<br />
<p>Router(config)#int fa0/0</p>
<p>Router(config-if)#ip address 192.168.2.1 255.255.255.0</p>
<p>Router(config-if)# no shutdown</p>
<p>Router(config-if)#exit</p>
<br />
<p>Router(config)#router ospf 1</p>
<p>Router(config-router)#network 192.168.2.0 0.0.0.255 area 0</p>
<p>Router(config-router)#network 172.16.0.0 0.0.0.3 area 0</p>
<p>Router(config-router)#exit</p>
<br />

<h2>Shrnutí</h2>
<p>Zatím jenom příkazy pro propagaci vlastních sítí v OSPF.</p>
