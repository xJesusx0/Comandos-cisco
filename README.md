### Comandos básicos de Cisco

#### Acceso a modos

##### Modo privilegiado

- Para acceder al modo privilegiado desde el modo EXEC de usuario:

    ```
    switch> enable
    ```

- Para volver al modo EXEC de usuario desde el modo privilegiado:

    ```
    switch# exit
    ```

##### Modo de configuración global

- Para acceder al modo de configuración global desde el modo privilegiado:

    ```
    switch# configure terminal
    ```

- Para volver al modo privilegiado desde el modo de configuración global:

    ```
    switch(config)# exit
    ```

### Visualización de configuraciones

- Mostrar la configuración en ejecución:

    ```
    switch# show running-config
    ```

- Mostrar la configuración de inicio:

    ```
    switch# show startup-config
    ```

### Configuración de interfaz

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

- Salir del modo de configuración de interfaz:

    ```
    switch(config-if)# end
    ```

### Cambio de nombre

- Cambiar el nombre del dispositivo:

    ```
    switch(config)# hostname nombre
    ```

- Quitar el nombre del dispositivo:

    ```
    switch(config)# no hostname
    ```

### Contraseñas

#### Contraseña de modo usuario

- Configurar la contraseña de modo usuario:

    ```
    switch(config)# line console 0
    switch(config-line)# password contraseña
    ```

- Activar la solicitud de contraseña al entrar en modo EXEC de usuario:

    ```
    switch(config-line)# login
    ```

- Salir del modo de configuración de línea:

    ```
    switch(config-line)# end
    ```

#### Contraseña de modo privilegiado

- Configurar la contraseña de modo privilegiado:

    ```
    switch# configure terminal
    switch(config)# enable secret contraseña
    ```

- Salir del modo de configuración global:

    ```
    switch(config)# end
    ```

#### Contraseña remota

- Configurar la contraseña para acceso remoto:

    ```
    switch# configure terminal
    switch(config)# line vty 0 15
    switch(config-line)# password contraseña
    ```

- Activar la solicitud de contraseña al acceder de forma remota:

    ```
    switch(config-line)# login
    ```

- Salir del modo de configuración de línea:

    ```
    switch(config-line)# end
    ```

### Encriptación de contraseñas

- Encriptar las contraseñas:

    ```
    switch# show run
    switch# configure terminal
    switch(config)# service password-encryption
    ```

- Salir del modo de configuración global:

    ```
    switch(config)# end
    ```

### Guardar configuración y reiniciar

- Guardar la configuración actual en la memoria no volátil:

    ```
    switch# copy running-config startup-config
    ```

- Reiniciar el dispositivo:

    ```
    switch# reload
    ```

### Mensajes de bienvenida

- Configurar un mensaje de bienvenida:

    ```
    switch# configure terminal
    switch(config)# banner motd #Acceso autorizado únicamente. Los infractores se procesarán en la medida en que lo permita la ley.#
    ```

### Formateo (¡Usar con cuidado!)

- Formatear la configuración de inicio (elimina toda la configuración):

    ```
    switch# erase startup-config
    ```

### Configuración de IP

#### En un switch

- Configurar la dirección IP de una interfaz VLAN:

    ```
    Switch#configure terminal
    Switch(config)#int vlan vlan-number
    Switch(config-if)#ip address ip-address subnet-mask
    Switch(config-if)#no shutdown
    ```

#### En un router

- Configurar la dirección IP de una interfaz:

    ```
    Router#configure terminal
    Router(config)#interface interface-type/number
    Router(config-if)#ip address direccion mascara-de-subred
    Router(config-if)#no shutdown
    ```

- Ponerle descripción a una interfaz:

    ```
    Router(config-if)#description Texto cualquier
    Router(config-if)#end
    ```

- Ruta de salida del router:

    ```
    Router#configure terminal
    Router(config)#ip route 0.0.0.0 0.0.0.0 ip-router 
    ```

    Ambos routers deben configurarse.

    - Ejemplo:
      - Router 1 - ip = 1.1.1.1
      - Router 2 - ip = 2.2.2.2
  
    - Agregamos la ip del router 2 al router 1:

        ```
        Router1(config)#ip route 0.0.0.0 0.0.0.0 2.2.2.2 
        ```

    - Agregamos la ip del router 1 al router 2:

        ```
        Router2(config)#ip route 0.0.0.0 0.0.0.0 1.1.1.1 
        ```

- Ver estado de las interfaces:

    ```
    Router#show interface
    ```

- Para ver una interfaz en específico:

    ```
    Router#show interface serial 0/0/0
    Router#show interface fastEthernet 0/1
    ```

- Ver estado de la interfaz y las direcciones IP asignadas a ellas:

    ```
    Router#show ip interface brief
    ```

- Ver tabla de enrutamiento:

    ```
    Router#show ip route
    ```

- Para ver solo las que están conectadas:

    ```
    Router#show ip route c
    ```

### Configurar router DHCP

- Excluir una dirección IP
  - Ejemplo 1:

    ```
    Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
    ```

  - Ejemplo 2:

    ```
    Router(config)# ip dhcp excluded-address 172.16.0.1 172.16.0.10
    ```

  ```
  Router(config)# ip dhcp excluded-address limite-inferior limite-superior
  ```

- Configurar un pool de direcciones:

  ```
  R1(config)# ip dhcp pool RED1
  R1(config)# network 192.168.1.0 255.255.255.0
  R1(config)# default-router 192.168.1.1
  R1(config)# dns-server 8.8.8.8
  ```

  - Ejemplo:

    ```
    R1(config)# ip dhcp pool Nombre-red
    R1(config)# network ip-red mascara-red
    R1(config)# default-router direccion-router
    R1(config)# dns-server 8.8.8.8
    ```