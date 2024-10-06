# Manual técnico
## Introducción
Después de realizar un buen trabajo para la empresa “Solución al Cliente S.A.”, el camino
de la vida lo guía hacia una nueva contratación, esta vez por la administración del Colegio
CiscoWorks, quienes desean expandir su oferta educativa y como resultado fue creada la
Academia Técnica de Formación Empresarial – ACATEC.

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
