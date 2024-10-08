# Manual técnico
## Introducción
El presente manual técnico tiene como objetivo detallar el proceso de diseño e implementación de una red local (LAN) para la municipalidad de Guatemala, siguiendo las especificaciones brindadas en el curso de Redes de Computadoras 1 de la Universidad de San Carlos de Guatemala. La red está compuesta por cuatro departamentos clave: Contabilidad, Secretaría, Recursos Humanos e Informática, los cuales están segmentados mediante VLANs para asegurar el aislamiento de tráfico y mejorar la seguridad.

Se emplearán tecnologías de redes avanzadas como VLANs, el protocolo de árbol de expansión (STP), y la configuración de VTP para asegurar la redundancia, prevenir bucles de red y optimizar el rendimiento. Además, se utilizará el software Packet Tracer para la simulación y diseño de la topología, así como Wireshark para la captura de paquetes que verifiquen el correcto funcionamiento de la red.

Este manual incluye los comandos necesarios para la configuración de los dispositivos de red, un resumen de las direcciones IP y VLANs asignadas, capturas de pantalla de la implementación, y pruebas de conectividad entre hosts de diferentes VLANs. Finalmente, se presenta un presupuesto detallado del equipo necesario para llevar a cabo la implementación física de la red propuesta.

## Topología de red

### Centro administrativo
![adminCenter](img/centro_administrativo.png)

### Área de trabajo
![workstation](img/area_trabajo.png)

### BackBone
![backbone](img/backbone.png)


## Configuración de las VTP
### Comandos utilizados
- enable
- configure terminal
- vtp mode <server | transparent | client>
- vtp domain P11
- vtp password usac
- vtp version 2
- exit
- wr

Para verificar la configuración en el switch se deberá ingresar el siguiente comando:
- show vtp status

### BackBone
![vtp01](img/vtp01.png)
![vtp02](img/vtp02.png)
![vtp03](img/vtp03.png)
![vtp04](img/vtp04.png)
![vtp05](img/vtp05.png)
![vtp06](img/vtp06.png)

### Centro administrativo
![vtp07](img/vtp07.png)
![vtp08](img/vtp08.png)
![vtp09](img/vtp09.png)


### Área de trabajo
![alt text](img/image.png)
![alt text](img/image-1.png)
![alt text](img/image-2.png)

## Modo troncal
### Comandos utilizados
- enable
- configure terminal
- interface range f0/1-2 para este ejemplo
- switchport trunk encapsulation dot1q
- switchport mode trunk
- switchport trunk allowed vlan all
- exit
- exit
- wr

Para verificar la configuración en el switch se deberá ingresar el siguiente comando:
- show startup-config

![alt text](img/image-4.png)
![alt text](img/image-5.png)
![alt text](img/image-6.png)
![alt text](img/image-7.png)


## Configuración de las VLAN
### Comandos utilizados
- enable
- configure terminal
- vlan <26 | 36 | 46 | 56>
- name <contabilidad | secretaria | RRHH | IT>
- exit

repetir el proceso con cada una de las VLAN
- exit
- exit
- wr

![alt text](img/image-3.png)

## Ping entre áreas
- Ping entre RRHH

![pingRRHH](img/image-9.png)

- Ping entre secretaría

![ping_secretaria](img/image-10.png)

- Ping entre contabilidad

![ping_contabilidad](img/image-11.png)

- Ping entre IT

## SW9 de manera transparente 
### Comandos utilizados
- enable
- configure terminal
- vtp mode < transparent >
- vtp domain P11
- vtp password usac
- vtp version 2
- exit
- wr

Para verificar la configuración en el switch 9 de manera transparente deberá ingresar el siguiente comando:
- show vtp status

![TransparentMode](img/TransparentSW9.png)


## PING entre maquinas IT

Para verificar pings entre maquinas IT, se realizar el ping unicamente en las maquinas denominadas para esa area
- Se abre la consola 
- Se intoduce la ip 
- Se verifica que haya ping entre ambas maquinas

![ping_maquinasIT](img/IT1.jpeg)
![ping_maquinasIT](img/IT2.jpeg)

## Configuracion STP para switches 
- enable
- configure terminal
- spanning-tree mode rapid-pvst
- exit
- wr

Para verificar que tengan el STP activado se coloca el siguiente comando
-  show spannig-tree

![STP](img/STP.jpeg)
