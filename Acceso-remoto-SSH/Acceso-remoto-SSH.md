# Acceso-remoto-SSH

### (2.2) Primera conexión SSH GNU/Linux

- Ir al cliente `clientXXg`.

- `ping serverXXg`, comprobar la conectividad con el servidor.

- `nmap -Pn serverXXg`, comprobar los puertos abiertos en el servidor
(SSH debe estar open). Debe mostrarnos que el puerto 22 está abierto.
Debe aparecer una línea como "22/tcp open ssh".

![2.2]( )


- Si esto falla debemos comprobar en el servidor la configuración del
cortafuegos.

    Vamos a comprobar el funcionamiento de la conexión SSH desde cada
cliente usando el usuario 1er-apellido-alumno1.

- Desde el cliente GNU/Linux nos conectamos mediante ssh
1er-apellido-alumno1@serverXXg. Capturar imagen del intercambio de
claves que se produce en el primer proceso de conexión SSH.

![2.2.1]( )

- Si nos volvemos a conectar tendremos:

![2.2.2]( )

- Comprobar contenido del fichero `$HOME/.ssh/known_hosts `en el equipo
cliente. OJO el prompt nos indica en qué equipo estamos.

` `

### (3.2) Comprobar cambio clave servidor SSH

- Comprobar qué sucede al volver a conectarnos desde los dos clientes,
usando los usuarios 1er-apellido-alumno2 y 1er-apellido-alumno1.

### (5 ) Autenticación mediante clave pública
- Vamos a la máquina clientXXg.
- Iniciamos sesión con nuestro el usuario nombre-alumno de la máquina
clientXXg.
`ssh-keygen -t` rsa para generar un nuevo par de claves para el usuario
en:
  - `/home/nombre-alumno/.ssh/id_rsa`
  - `/home/nombre-alumno/.ssh/id_rsa.pub`

- Ahora vamos a copiar la clave pública (id_rsa.pub), al fichero
"authorized_keys" del usuario remoto 1er-apellido-alumno4 que está
definido en el servidor.

  - Hay varias formas de hacerlo.
  - El modo recomendado es usando el comando `ssh-copy-id`. Ejemplo para
copiar la clave pública del usuario actual al usuario remoto en la
máquina remota: `ssh-copy-id 1er-apellido-alumno4@serverXXg`.

- Comprobar que ahora al acceder remotamente vía SSH
  - Desde `clientXXg`, NO se pide password.
  - Desde `clientXXw`, SI se pide el password.

### (6 ) Uso de SSH como túnel para X

- Modificar servidor SSH para permitir la ejecución de aplicaciones
gráficas, desde los clientes. Consultar fichero de configuración`
/etc/ssh/sshd_config` (Opción X11Forwarding yes)

- Reiniciar el servicio SSH para que se lean los cambios de
configuración.

Vamos a clientXXg.

- `zypper se APP1`,comprobar que no está instalado el programa APP1.
- Vamos a comprobar desde clientXXg, que funciona APP1(del servidor).
`ssh -X primer-apellido-alumno1@serverXXg`, nos conectamos de forma
remota al servidor, y ahora ejecutamos APP1 de forma remota.		

### (8.1) Restricción sobre un usuario

#### 8.1 Restricción sobre un usuario
Vamos a crear una restricción de uso del SSH para un usuario:

- En el servidor tenemos el usuario primer-apellido2. Desde local en el
servidor podemos usar sin problemas el usuario.

- Vamos a modificar SSH de modo que al usar el usuario por SSH desde los
clientes tendremos permiso denegado.

Capturar imagen de los siguientes pasos:

- Consultar/modificar fichero de configuración del servidor SSH
`(/etc/ssh/sshd_config)` para restringir el acceso a determinados
usuarios. Consultar las opciones` AllowUsers, DenyUsers (Más información
en: man sshd_config)`

- `/usr/sbin/sshd -t; echo $?,` comprobar si la sintaxis del fichero de
configuración del servicio SSH es correcta (Respuesta 0 => OK, 1 =>
ERROR).

- Comprobarlo la restricción al acceder desde los clientes.

#### 8.2 Restricción sobre una aplicación

- Vamos a crear una restricción de permisos sobre determinadas
aplicaciones.

- Crear grupo `remoteapps`

- Incluir al usuario `1er-apellido-alumno4 `en el grupo `remoteapps`.

- Localizar el programa APP1. Posiblemente tenga permisos 755.

- Poner al programa APP1 el grupo propietario a remoteapps.

- Poner los permisos del ejecutable de APP1 a 750. Para impedir que los
usuarios que no pertenezcan al grupo puedan ejecutar el programa.

- Comprobamos el funcionamiento en el servidor en local.
- Comprobamos el funcionamiento desde el cliente en remoto (Recordar
`ssh -X ...`).
