
```markdown
### Modo exec de usuario

```
switch>
```

Solo comandos básicos para ver configuraciones:

```shell
$ Para pasar al modo privilegiado se debe escribir
```
switch>enable
```
---
#### Modo privilegiado

```shell
switch#
```

```shell
$ Para volver al modo usuario
```
switch# exit
```

```shell
$ Para pasar al modo de configuración global
```
switch# configure terminal
```
---
#### Modo de configuración global

```shell
switch(config)#
```

```shell
$ Para volver al modo privilegiado
```
switch(config)# exit
```

Acceso a todas las configuraciones:

```shell
$ Para ir al configuración de interfaz
```
switch(config)# interface fastethernet0/n
```
---
#### Modo de configuración de interfaz

```shell
switch(config-if)#
```

```shell
$ Apagar un dispositivo
```
switch(config-if)# shutdown
```
```shell
$ Encender
```
switch(config-if)# no shutdown
```

```shell
$ Salir
```
switch(config-if)# end
```

```shell
$ Cambiar nombre
```
switch(config)# hostname nombre
```
nombre(config)#
```

```shell
$ Para poner primera contraseña modo usuario
```
switch(config)# line console 0
switch(config-line)# password contraseña
```
```shell
$ Para que la pida al entrar
```
switch(config-line)# login
switch(config-line)# end
```

```shell
$ Poner contraseña modo privilegiado
```
switch# configure terminal
switch(config)# enable secret contraseña
switch(config)# end
```

```shell
$ Configurar contraseña remota
```
switch# configure terminal
switch(config)# line vty 0 15
switch(config-line)# password contraseña
switch(config-line)# login
switch(config-line)# end
```

```shell
$ Encriptar las contraseñas
```
switch# show run
switch# configure terminal
switch(config)# service password-encryption 
switch-(config)# end
```

```shell
$ Guardar las configuraciones
```
switch# copy running-config startup-config
```

```shell
$ Reiniciar 
```
switch# reload
```

```shell
$ Poner mensaje
```
switch# configure terminal
switch(config)# banner motd #Acceso autorizado únicamente. Los infractores se procesarán en la medida en que lo permita la ley.#
```

```shell
$ FORMATEAR (USAR CON CUIDADO)
```
switch# erase startup-config 
```

```shell
$ Poner IP en Switch
```
Switch# configure terminal
Switch(config)# int vlan 1
Switch(config-if)# ip address 192.168.1.10 255.255.255.0
Switch(config-if)# no shutdown
```

```shell
$ Configurar Router
```

```shell
$ Poner IP en Router
```
Router# configure terminal
Router(config)# interface G0/0/1
Router(config-if)# ip address 192.168.1.10 255.255.255.0
Router(config-if)# no shutdown
```

Esto debería darte un formato Markdown adecuado para tu texto. Por favor, revisa y ajusta según sea necesario.
