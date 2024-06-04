### Acceso a modos

- **Modo privilegiado**:
    - Acceder: `switch> enable`
    - Volver: `switch# exit`

- **Modo de configuración global**:
    - Acceder: `switch# configure terminal`
    - Volver: `switch(config)# exit`

### Visualización de configuraciones

- **Mostrar configuración**:
    - En ejecución: `switch# show running-config`
    - De inicio: `switch# show startup-config`
    - Interfaces: `switch# show interfaces [interface-id]`
    - Flash: `switch# show flash`
    - Sistema: `switch# show version`
    - Direcciones IP: `switch# show ip interface [interface-id]`
    - Tabla de direcciones MAC: `switch# show mac-address-table`
    - Tabla de enrutamiento: `R1# show ip route`
    - IP de subinterfaces: `R1# show ip interface brief`
    - Detalles de subinterfaces: `R1# show interfaces g0/0/1.10`
    - Enlaces troncales: `S1# show interfaces trunk`

### Configuración de interfaz

- **Acceder al modo de configuración de interfaz**:
    - `switch(config)# interface interface-type/number`

- **Gestión de interfaz**:
    - Apagar: `switch(config-if)# shutdown`
    - Encender: `switch(config-if)# no shutdown`
    - Configurar default gateway: `S1(config)# ip default-gateway 192.168.1.1`

### Cambio de nombre

- **Cambiar nombre del dispositivo**:
    - `switch(config)# hostname nombre`
- **Quitar nombre del dispositivo**:
    - `switch(config)# no hostname`

### Contraseñas

- **Contraseña de modo usuario**:
    - Configurar: `switch(config)# line console 0`, `switch(config-line)# password contraseña`
    - Solicitar contraseña: `switch(config-line)# login`
- **Contraseña de modo privilegiado**:
    - Configurar: `switch(config)# enable secret contraseña`
- **Contraseña remota**:
    - Configurar: `switch(config)# line vty 0 15`, `switch(config-line)# password contraseña`
    - Activar solicitud: `switch(config-line)# login`

### Encriptación de contraseñas

- **Encriptar contraseñas**:
    - `switch(config)# service password-encryption`

### Guardar configuración y reiniciar

- **Guardar configuración**:
    - `switch# copy running-config startup-config`
- **Reiniciar dispositivo**:
    - `switch# reload`

### Mensajes de bienvenida

- **Configurar mensaje de bienvenida**:
    - `switch(config)# banner motd #Mensaje aquí#`

### Formateo (¡Usar con cuidado!)

- **Formatear configuración de inicio**:
    - `switch# erase startup-config`
- **Eliminar archivo de VLAN**:
    - `switch# delete vlan.dat`

### Configuración de IP

- **En un switch**:
    - Configurar dirección IP de una interfaz VLAN: `Switch(config)#int vlan vlan-number`, `Switch(config-if)#ip address ip-address subnet-mask`, `Switch(config-if)#no shutdown`
    - Ver estado de las VLAN: `Router#show vlan brief`
- **En un router**:
    - Configurar dirección IP de una interfaz: `Router(config)#interface interface-type/number`, `Router(config-if)#ip address direccion mascara-de-subred`, `Router(config-if)#no shutdown`
    - Descripción de interfaz: `Router(config-if)#description Texto cualquier`
    - Ruta de salida: `Router(config)#ip route 0.0.0.0 0.0.0.0 ip-router`
    - Ver estado de interfaces: `Router#show interface`
    - Ver estado de IP: `Router#show ip interface brief`
    - Ver tabla de enrutamiento: `Router#show ip route`

### Configuración de router DHCP

- **Excluir dirección IP**: `Router(config)# ip dhcp excluded-address limite-inferior limite-superior`
- **Configurar pool de direcciones**: `Router(config)# ip dhcp pool Nombre-red`, `Router(dhcp-config)# network ip-red mascara-red`, `Router(dhcp-config)# default-router direccion-router`, `Router(dhcp-config)# dns-server 8.8.8.8`

### Acceso SSH

- **Verificar SSH**: `S1# show ip ssh`
- **Asignar nombre de dominio**: `S1(config)# ip domain-name nombre-dominio`
- **Generar claves RSA**: `S1(config)# crypto key generate rsa`
- **Configurar autenticación de usuarios**: `S1(config)# username usuario secret contraseña`
- **Configurar líneas vty**: `S1(config)# line vty 0 15`, `S1(config-line)# transport input ssh`, `S1(config-line)# login local`
- **Eliminar contraseña**: `S1(config-line)#no password contraseña`
- **Habilitar SSH versión 2**: `S1(config)# ip ssh version 2`

### VLAN

- **Crear VLAN**: `S1(config)# vlan 99`, `S1(config-vlan)# name nombre-vlan`
- **Asignar puerto a VLAN**: `S1(config)# interface fa0/6`, `S1(config-if)# switchport mode access`, `S1(config-if)# switchport access vlan 99`
- **Quitar puerto de VLAN**: `S1(config)# interface fa0/18`, `S1(config-if)# no switchport access vlan`
- **Eliminar VLAN**: `S1# no vlan vlan-id`
- **Asignar varios puertos a VLAN**: `S1(config)#interface range gig1/0/1-24`, `S1(config-if-range)#switchport access vlan 99`
- **Ver todas las VLAN**: `S1# show vlan`
- **Configurar VLAN de voz y datos**: ver subsección correspondiente
- **Configurar enlace troncal**: ver subsección correspondiente

### Configuración de EtherChannel

- **Configurar EtherChannel**: ver subsección correspondiente
- **Ver información sobre EtherChannel**: ver subsección correspondiente
