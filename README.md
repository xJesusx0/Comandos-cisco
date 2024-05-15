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

## Configuración de IP

### En un switch

- Configurar la dirección IP de una interfaz VLAN:

    ```
    Switch(config)#int vlan vlan-number
    Switch(config-if)#ip address ip-address subnet-mask
    Switch(config-if)#no shutdown
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
    S1(config)# ip domain-name cisco.com
    ```

- Generar claves RSA:

    ```
    S1(config)# crypto key generate rsa
    ```

- Configurar autenticación de usuarios:

    ```
    S1(config)# username admin secret ccna
    ```

- Configurar las líneas vty:

    ```
    S1(config)# line vty 0 15
    S1(config-line)# transport input ssh
    S1(config-line)# login local
    ```

- Habilitar SSH versión 2:

    ```
    S1(config)# ip ssh version 2
    ```
## Otros

-  Asignar todos los puertos de usuario a VLAN 99.
    ```
    S1(config)#interface range gig1/0/1-24
    S1(config-if-range)#swi
    S1(config-if-range)#switchport access vlan 99
    ```
