# Acceso-remoto-SSH

### (2.2) Primera conexión SSH GNU/Linux

- Ir al cliente `clientXXg`.

- `ping serverXXg`, comprobar la conectividad con el servidor.

- `nmap -Pn serverXXg`, comprobar los puertos abiertos en el servidor
(SSH debe estar open). Debe mostrarnos que el puerto 22 está abierto.
Debe aparecer una línea como "22/tcp open ssh".

![2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/2.2.png?raw=true)



### (5 ) Autenticación mediante clave pública
- Vamos a la máquina clientXXg.
- Iniciamos sesión con nuestro el usuario nombre-alumno de la máquina
clientXXg.
`ssh-keygen -t rsa` para generar un nuevo par de claves para el usuario
en:
  - `/home/nombre-alumno/.ssh/id_rsa`
  - `/home/nombre-alumno/.ssh/id_rsa.pub`

![5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/2.2.2.3.png?raw=true)


  - El modo recomendado es usando el comando `ssh-copy-id`. Ejemplo para
copiar la clave pública del usuario actual al usuario remoto en la
máquina remota: `ssh-copy-id 1er-apellido-alumno4@serverXXg`.

![5.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/Captura%20de%20pantalla_2020-10-19_09-13-58.png?raw=true)

### (6 ) Uso de SSH como túnel para X

- Modificar servidor SSH para permitir la ejecución de aplicaciones
gráficas, desde los clientes. Consultar fichero de configuración`
/etc/ssh/sshd_config` (Opción X11Forwarding yes)`
![6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/Captura%20de%20pantalla_2020-10-19_09-15-59.png?raw=true)
- Reiniciar el servicio SSH para que se lean los cambios de
configuración.

Vamos a clientXXg.

- `zypper se APP1`,comprobar que no está instalado el programa APP1.


 ![6.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/6.1.png?raw=true)

- Vamos a comprobar desde clientXXg, que funciona APP1(del servidor).
`ssh -X primer-apellido-alumno1@serverXXg`, nos conectamos de forma
remota al servidor, y ahora ejecutamos APP1 de forma remota.		

![6.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/6.2.png?raw=true)




#### 8.1 Restricción sobre un usuario

- Consultar/modificar fichero de configuración del servidor SSH
`(/etc/ssh/sshd_config)` para restringir el acceso a determinados
usuarios. Consultar las opciones` AllowUsers, DenyUsers (Más información
en: man sshd_config)`

![8.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/Captura%20de%20pantalla_2020-10-19_10-13-50.png?raw=true)


- `/usr/sbin/sshd -t; echo $?,` comprobar si la sintaxis del fichero de
configuración del servicio SSH es correcta (Respuesta 0 => OK, 1 =>
ERROR).

![8.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/8.1.png?raw=true)

#### 8.2 Restricción sobre una aplicación

- Crear grupo `remoteapps`
    - En la captura no lo agrego pero antes de esa captura se ejecuta el comando `groupadd remoteapps` para crear dicho grupo por modo comando antes de nada.

![8.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/8.2.png?raw=true)


- Incluir al usuario `1er-apellido-alumno4 `en el grupo `remoteapps`.
![2.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/8.2.1.png?raw=true)

- Localizar el programa APP1. Posiblemente tenga permisos 755.

- Poner al programa APP1 el grupo propietario a remoteapps.

- Poner los permisos del ejecutable de APP1 a 750. Para impedir que los
usuarios que no pertenezcan al grupo puedan ejecutar el programa.

- Comprobamos el funcionamiento en el servidor en local.
- Comprobamos el funcionamiento desde el cliente en remoto (Recordar
`ssh -X ...`).

![8.2.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Acceso-remoto-SSH/img/8.2.3.png?raw=true)
