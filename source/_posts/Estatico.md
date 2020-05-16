---
title: Ruteo Estático
date: 2020-05-16 00:13:26
tags:
---

# Ruteo Estático

A diferencia de un protocolo de enrutamiento dinámico, las rutas estáticas no se actualizan automáticamente y deben reconfigurarse manualmente cada vez que cambia la topología de la red. Una ruta estática no cambia hasta que el administrador la reconfigura manualmente.

El enrutamiento estático ofrece algunas ventajas sobre el enrutamiento dinámico, que incluyen:



*   Las rutas estáticas no se anuncian a través de la red, lo que resulta en una mejor seguridad.
*   Las rutas estáticas usan menos ancho de banda que los protocolos de enrutamiento dinámico, ya que los enrutadores no intercambian rutas.
*   No se utilizan ciclos de CPU para calcular y comunicar rutas.
*   La ruta que utiliza una ruta estática para enviar datos es conocida.

El enrutamiento estático tiene las siguientes desventajas:



*   La configuración inicial y el mantenimiento requieren mucho tiempo.
*   La configuración puede ser propensa a errores, especialmente en redes grandes.
*   Se requiere la intervención del administrador para mantener la información de ruta cambiante.
*   No escala bien con redes en crecimiento; El mantenimiento se vuelve engorroso.
*   Requiere un conocimiento completo de toda la red para una implementación adecuada.



![alt_text](images/Copia-de4.png "image_tooltip")



## Paso 1: Configurar ip estaticas en cada interfaz

**Router R1**

**Port f0/0**

R1#configure terminal

R1(config)#interface fastEthernet 0/0

R1(config-if)#ip address 60.61.62.1 255.255.255.0

R1(config-if)#no shutdown

R1(config-if)#exit

**Port f0/1**

R1#configure terminal

R1(config)#interface fastEthernet 0/1

R1(config-if)# ip address 192.168.1.1 255.255.255.0

R1(config-if)no shutdown

R1(config-if)#exit

R1(config)#exit

**Router R2**

**Port f0/0**

R2#configure terminal 

R2(config)#interface fastEthernet 0/0

R2(config-if)#ip address 60.61.62.2 255.255.255.0

R2(config-if)#no shutdown

R2(config-if)#exit

**Port f0/1**

R2#configure terminal 

R2(config)#interface fastEthernet 0/1

R2(config-if)#ip address 10.11.12.1 255.255.255.0

R2(config-if)#no shutdown

R2(config-if)#exit

**Router R3**

**Port f0/0**

R3#configure terminal 

R3(config)#interface fastEthernet 0/0

R3(config-if)#ip address 10.11.12.2  255.255.255.0

R3(config-if)#no shutdown

R3(config-if)#exit

**Port f0/1**

R3#configure terminal 

R3(config)#interface fastEthernet 0/1

R3(config-if)#ip address 172.16.1.1 255.255.255.0

R3(config-if)#no shutdown

R3(config-if)#exit


## Paso 2: Configurar ips en las PC

**PC1**
```

ip 192.168.1.2 255.255.255.0 192.168.1.1 (ip-subnetmask-gw)
```

**PC2**
```

ip 172,16,1,2 255.255.255.0 172.16.1.1 (ip-subnetmask-gw)
```


## Paso 3: Configurar ruteo estático

**Router R1**
```

R1#configure terminal

R1(config)#ip route 10.11.12.0 255.255.255.0 f0/0

R1(config)#ip route 172.16.1.0 255.255.255.0 f0/0

R1(config)#exit

R1# show ip route
```

**Router R2**
```

R2#configure terminal

R2(config)#ip route 192.168.1.0.0 255.255.255.0 f0/0

R2(config)#ip route 172.16.1.0 255.255.255.0 f0/1

R2(config)#exit

R2#show ip route
```

**Router R3**
```

R3#configure terminal

R3(config)#ip route 192.168.1.0.0 255.255.255.0 f0/0

R3(config)#ip route 60.61.62.0 255.255.255.0 f0/0

R3(config)#exit

R3#show ip route
```

Paso 4: Comprobar conexión entre PC1 y PC2
```

PC1> ping 172.16.1.2

84 bytes from 172.16.1.2 icmp_seq=1 ttl=61 time=50.222 ms

84 bytes from 172.16.1.2 icmp_seq=2 ttl=61 time=44.179 ms

84 bytes from 172.16.1.2 icmp_seq=3 ttl=61 time=38.323 ms

84 bytes from 172.16.1.2 icmp_seq=4 ttl=61 time=52.193 ms

84 bytes from 172.16.1.2 icmp_seq=5 ttl=61 time=52.702 ms
```
```

PC2> ping 192.168.1.2

84 bytes from 192.168.1.2 icmp_seq=1 ttl=61 time=64.201 ms

84 bytes from 192.168.1.2 icmp_seq=2 ttl=61 time=47.265 ms

84 bytes from 192.168.1.2 icmp_seq=3 ttl=61 time=54.286 ms

84 bytes from 192.168.1.2 icmp_seq=4 ttl=61 time=39.279 ms

84 bytes from 192.168.1.2 icmp_seq=5 ttl=61 time=46.208 ms
```
