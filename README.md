# Comandos básicos de Cisco

## Acceso a modos

### Modo privilegiado

- Para acceder al modo privilegiado desde el modo EXEC de usuario:

    ```
    switch> enable
    ```

- Para volver al modo EXEC de usuario desde el modo privilegiado:

    ```
    switch# exit
    ```

### Modo de configuración global

- Para acceder al modo de configuración global desde el modo privilegiado:

    ```
    switch# configure terminal
    ```

- Para volver al modo privilegiado desde el modo de configuración global:

    ```
    switch(config)# exit
    ```

## Visualización de configuraciones

- Mostrar la configuración en ejecución:

    ```
    switch# show running-config
    ```

- Mostrar la configuración de inicio:

    ```
    switch# show startup-config
    ```

- Muestra el estado y la configuración de la interfaz:

    ```
    switch# show interfaces [interface-id]
    ```

- Muestra información sobre el sistema de archivos flash:

    ```
    switch# show flash
    ```

- Muestra el estado del hardware y el software del sistema:

    ```
    switch# show version
    ```

- Muestra información de IP de una interfaz:

    ```
    switch# show ip interface [interface-id]
    ```

- Muestra la tabla de direcciones MAC:

    ```
    switch# show mac-address-table
    ```

## Configuración de interfaz

- Acceder al modo de configuración de interfaz:

    ```
    switch(config)# interface interface-type/number
    ```

- Apagar una interfaz:

    ```
    switch(config-if)# shutdown
    ```

- Encender una interfaz:

    ```
    switch(config-if)# no shutdown
    ```
- Poner default gateway:

    ```
    S1(config)# ip default-gateway 192.168.1.1
    ```
## Cambio de nombre

- Cambiar el nombre del dispositivo:

    ```
    switch(config)# hostname nombre
    ```

- Quitar el nombre del dispositivo:

    ```
    switch(config)# no hostname
    ```

## Contraseñas

### Contraseña de modo usuario

- Configurar la contraseña de modo usuario:

    ```
    switch(config)# line console 0
    switch(config-line)# password contraseña
    ```

- Activar la solicitud de contraseña al entrar en modo EXEC de usuario:

    ```
    switch(config-line)# login
    ```

### Contraseña de modo privilegiado

- Configurar la contraseña de modo privilegiado:

    ```
    switch(config)# enable secret contraseña
    ```

### Contraseña remota

- Configurar la contraseña para acceso remoto:

    ```
    switch(config)# line vty 0 15
    switch(config-line)# password contraseña
    ```
- Configurar contraseña para acceso remoto con telnet:
  
  ```
  S1(config)# line con 0
  S1(config-line)# logging synchronous
  ```
- Activar la solicitud de contraseña al acceder de forma remota:

    ```
    switch(config-line)# login
    ```

## Encriptación de contraseñas

- Encriptar las contraseñas:

    ```
    switch(config)# service password-encryption
    ```

## Guardar configuración y reiniciar

- Guardar la configuración actual en la memoria no volátil:

    ```
    switch# copy running-config startup-config
    ```

- Reiniciar el dispositivo:

    ```
    switch# reload
    ```

## Mensajes de bienvenida

- Configurar un mensaje de bienvenida:

    ```
    switch(config)# banner motd #Acceso autorizado únicamente. Los infractores se procesarán en la medida en que lo permita la ley.#
    ```

## Formateo (¡Usar con cuidado!)

- Formatear la configuración de inicio (elimina toda la configuración):

    ```
    switch# erase startup-config
    ```
- Eliminar el archivo que contiene las vlan:

    ```
    switch# delete vlan.dat
    ```
## Configuración de IP

### En un switch

- Configurar la dirección IP de una interfaz VLAN:

    ```
    Switch(config)#int vlan vlan-number
    Switch(config-if)#ip address ip-address subnet-mask
    Switch(config-if)#no shutdown
    ```
- Ver estado de las vlan:

    ```
    Router#show vlan brief
    ```

### En un router

- Configurar la dirección IP de una interfaz:

    ```
    Router(config)#interface interface-type/number
    Router(config-if)#ip address direccion mascara-de-subred
    Router(config-if)#no shutdown
    ```

- Ponerle descripción a una interfaz:

    ```
    Router(config-if)#description Texto cualquier
    ```

- Ruta de salida del router:

    ```
    Router(config)#ip route 0.0.0.0 0.0.0.0 ip-router 
    ```

- Ver estado de las interfaces:

    ```
    Router#show interface
    ```

- Ver estado de la interfaz y las direcciones IP asignadas a ellas:

    ```
    Router#show ip interface brief
    ```

- Ver tabla de enrutamiento:

    ```
    Router#show ip route
    ```

### Configurar router DHCP

- Excluir una dirección IP:

    ```
    Router(config)# ip dhcp excluded-address limite-inferior limite-superior
    ```

- Configurar un pool de direcciones:

    ```
    Router(config)# ip dhcp pool Nombre-red
    Router(dhcp-config)# network ip-red mascara-red
    Router(dhcp-config)# default-router direccion-router
    Router(dhcp-config)# dns-server 8.8.8.8
    ```

## Acceso SSH

- Verificar compatibilidad con SSH:

    ```
    S1# show ip ssh
    ```

- Asignar nombre de dominio:

    ```
    S1(config)# ip domain-name nombre-dominio
    ```

- Generar claves RSA:

    ```
    S1(config)# crypto key generate rsa
    ```

- Configurar autenticación de usuarios:

    ```
    S1(config)# username usuario secret contraseña
    ```

- Configurar las líneas vty:

    ```
    S1(config)# line vty 0 15
    S1(config-line)# transport input ssh
    S1(config-line)# login local
    ```
- Eliminar una contraseña
  ```
  S1(config-line)#no password contraseña
  ```
- Habilitar SSH versión 2:

    ```
    S1(config)# ip ssh version 2
    ```
## Vlan
- Crear una vlan
  ```
  S1# configure terminal
  S1(config)# vlan 99
  S1(config-vlan)# name nombre-vlan
  S1(config-vlan)# end
  ```
  
- Asignar un puerto especifico a VLAN 99.
  ```
  S1# configure terminal
  S1(config)# interface fa0/6
  S1(config-if)# switchport mode access
  S1(config-if)# switchport access vlan 99
  S1(config-if)# end
  ```
  
- Ver en que vlan esta configurado un puerto
  ```
  S1# show interfaces fa0/18 switchport
  ```

- Quitar un puerto de una vlan, este sera asociado a la vlan por defecto
  ```
  S1(config)# interface fa0/18
  S1(config-if)# no switchport access vlan
  S1(config-if)# end
  ```
  Nota: Aunque la vlan ya no tenga puertos asignados, esta seguira activa

- Eliminar una vlan
  ```
  S1# no vlan vlan-id
  ```

- Asignar varios puertos a VLAN 99.
  ```
  S1(config)#interface range gig1/0/1-24
  S1(config-if-range)#switchport access vlan 99
  ```
  
- Ver todas las vlan configuradas
  ```
  S1# show vlan
  ```

- Configurar una vlan de voz y datos
  * Creacion de la vlan
  ```
  S3(config)# vlan 20
  S3(config-vlan)# name student
  S3(config-vlan)# vlan 150
  S3(config-vlan)# name VOICE
  S3(config-vlan)# exit
  ```
  
  * Asignar el puerto 18 a la vlan 
  ```
  S3(config)# interface fa0/18
  S3(config-if)# switchport mode access

  # Recibe datos de la vlan 20 y voz de la 150
  
  S3(config-if)# switchport access vlan 20
  S3(config-if)# mls qos trust cos
  S3(config-if)# switchport voice vlan 150
  S3(config-if)# end
  ```
- Configurar un enlace troncal
  ```
  S1(config)#int g0/1
  S1(config-if)#switchport mode trunk
  S1(config-if)#switchport trunk native vlan 99
  ```
- Configurar un enlace troncal dinamico
  ```
  S1(config)# interface g0/1
  S1(config-if)# switchport mode dynamic desirable
  ```
- Desactivar negociacion DTP
  ```
  S1(config-if)# switchport nonegotiate
  ```
