## Comandos básicos de Cisco

### Acceso a modos

#### Modo privilegiado

- Para acceder al modo privilegiado desde el modo EXEC de usuario:
    ```
    switch> enable
    ```

- Para volver al modo EXEC de usuario desde el modo privilegiado:
    ```
    switch# exit
    ```

#### Modo de configuración global

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
    Router(config-if)#ip address ip-address subnet-mask
    Router(config-if)#no shutdown
    ```
### Ruta de salida del router
    ```
    Router#configure terminal
    Router(config)#ip route 0.0.0.0 0.0.0.0 1.1.1.2 
    ```
## Notas

- Este documento solo incluye comandos básicos de Cisco. Para obtener información más detallada sobre un comando específico, consulte la documentación oficial de Cisco.
- Se recomienda usar el comando `help` para obtener información sobre la sintaxis y las opciones de
