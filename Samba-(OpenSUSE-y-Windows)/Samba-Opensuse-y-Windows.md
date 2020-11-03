- Nota:
  - Las ip de Clase:
    - server06g:172.19.6.31
    - client06g:172.19.6.32
    - client06w:172.19.06.11
  - Las ip de Casa:
    - server06g:192.168.0.61
    - client06g:192.168.0.62
    - client06w:172.19.0.71


### 1.4 Configurar el servidor Samba
Para instalar y configurar el servicio Samba, podemos usar comandos o el entorno gráfico. Como estamos en OpenSUSE vamos a usar Yast.

 - _cp /etc/samba/smb.conf /etc/samba/smb.conf.bak_, hacer una copia de seguridad del fichero de configuración antes de modificarlo.

 ![1.4.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-34-20.png?raw=true)

 - Yast -> Samba Server

 ![1.4.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-32-51.png?raw=true)


 - Workgroup: curso2021.
 Sin controlador de dominio.
![1.4.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-34-55.png?raw=true)

 - Comprobación del Cortafuegos. En la pestaña de Inicio definimos
Iniciar el servicio durante el arranque de la máquina.
Ajustes del cortafuegos -> Abrir puertos
Comprobar CORTAFUEGOS

 ![1.4.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-35-29.png?raw=true)



 -Para descartar un problema del servidor Samba con el cortafuegos, usaremos el comando nmap -Pn IP-servidor-Samba desde otra máquina GNU/Linux. Los puertos SMB/CIFS (139 y 445) deben estar abiertos.

 ![1.4.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/1.4.5.PNG?raw=true)

### 1.5 Crear los recursos compartidos de red


- Tenemos que conseguir una configuración con las secciones: global, public, barco, y castillo como la siguiente:

 - Donde pone XX, sustituir por el número del puesto de cada uno.

 - public, será un recurso compartido accesible para todos los usuarios en modo lectura.

 - barco, recurso compartido de red de lectura/escritura para todos los piratas.

 - castillo, recurso compartido de red de lectura/escritura para todos los soldados.


- Podemos modificar la configuración:
(a) Editando directamente el ficher /etc/samba/smb.conf o
(b) Yast -> Samba Server -> Recursos compartidos -> Configurar.

 ![1.5.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-52-38.png?raw=true)

 ![1.5.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-52-53.png?raw=true)


- testparm, verificar la sintaxis del fichero de configuración.

 ![1.5.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-53-44.png?raw=true)

 ![1.5.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-53-58.png?raw=true)


- more /etc/samba/smb.conf, consultar el contenido del fichero de configuración.

 ![1.5.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-54-36.png?raw=true)

 ![1.5.6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-10-27_12-54-57.png?raw=true)


### 2.1 Cliente Windows GUI
Desde un cliente Windows vamos a acceder a los recursos compartidos del servidor Samba.

  - Escribimos \\ip-del-servidor-samba y vemos lo siguiente:

   ![2.1.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-11-02_09-06-59.png?raw=true)

Capturar imagen de los siguientes comandos para comprobar los resultados:

  - smbstatus, desde el servidor Samba.
    ![2.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura.PNG?raw=true)

  - lsof -i, desde el servidor Samba.
    ![2.1.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura-2.PNG?raw=true)


### 2.2 Cliente Windows comandos
Capturar imagen de los comandos siguientes:
- net view \\IP-SERVIDOR-SAMBA, para ver los recursos de esta máquina.

 ![2.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/Captura%20de%20pantalla_2020-11-02_09-17-25.png?raw=true)


Montar el recurso barco de forma persistente.

- net use S: \\IP-SERVIDOR-SAMBA\recurso contraseña /USER:usuario /p:yes crear una conexión con el recurso compartido y lo monta en la unidad S.Con la opción /p:yes hacemos el montaje persistente. De modo que se mantiene en cada reinicio de máquina.

 ![2.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/2.2.2.PNG?raw=true)
- net use, comprobamos.
 ![2.2.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/2.2.3.PNG?raw=true)

Capturar imagen de los siguientes comandos para comprobar los resultados:
- smbstatus, desde el servidor Samba.
- lsof -i, desde el servidor Samba.

![2.2.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/2.2.4.PNG?raw=true)




### 3.1 Cliente GNU/Linux GUI
Pulsamos CTRL+L y escribimos smb://IP-SERVIDOR-SAMBA:
![3.1.0](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/3.1.png?raw=true)

![3.1.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/3.1.5.PNG?raw=true)

En el momento de autenticarse para acceder al recurso remoto, poner en Dominio el nombre-netbios-del-servidor-samba.

Capturar imagen de lo siguiente:

Probar a crear carpetas/archivos en castillo y en barco.
![3.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/3.1.2.PNG?raw=true)



Comprobar que el recurso public es de sólo lectura.

![3.1.6]()






Capturar imagen de los siguientes comandos para comprobar los resultados:
smbstatus, desde el servidor Samba.

![3.1.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/3.1.3.PNG?raw=true)


sudo lsof -i, desde el servidor Samba.

![3.1.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Samba-(OpenSUSE-y-Windows)/img/3.1.4.PNG?raw=true)

### 3.2 Cliente GNU/Linux comandos
Capturar imagenes de todo el proceso.

Existen comandos (smbclient, mount , smbmount, etc.) para ayudarnos a acceder vía comandos al servidor Samba desde el cliente. Puede ser que con las nuevas actualizaciones y cambios de las distribuciones alguno haya cambiado de nombre. ¡Ya lo veremos!

Vamos a un equipo GNU/Linux que será nuestro cliente Samba. Desde este equipo usaremos comandos para acceder a la carpeta compartida.
Probar desde una máquina Ubuntu sudo smbtree (REVISAR: no muestra nada)
Esto muestra todos los equipos/recursos de la red SMB/CIFS.
Hay que parar el cortafuegos para que funcione (systemctl stop firewalld), o bien
ejecutar comando desde la máquina real.
Probar desde OpenSUSE: smbclient --list IP-SERVIDOR-SAMBA, Muestra los recursos SMB/CIFS de un equipo.
Ahora crearemos en local la carpeta /mnt/remotoXX/castillo.
MONTAJE MANUAL: Con el usuario root, usamos el siguiente comando para montar un recurso compartido de Samba Server, como si fuera una carpeta más de nuestro sistema: mount -t cifs //172.AA.XX.31/castillo /mnt/remotoXX/castillo -o username=soldado1
En versiones anteriores de GNU/Linux se usaba el comando: smbmount //172.AA.XX.31/public /mnt/remotoXX/public/ -o -username=sambaguest.

df -hT, para comprobar que el recurso ha sido montado.
samba-linux-mount-cifs

Si montamos la carpeta de castillo, lo que escribamos en /mnt/remotoXX/castillo debe aparecer en la máquina del servidor Samba. ¡Comprobarlo!
Para desmontar el recurso remoto usamos el comando umount.
Capturar imagen de los siguientes comandos para comprobar los resultados:
smbstatus, desde el servidor Samba.
sudo lsof -i, desde el servidor Samba.

### 3.3 Montaje automático
Hacer una instantánea de la MV antes de seguir. Por seguridad.
Capturar imágenes del proceso.
Reiniciar la MV.
df -hT. Los recursos ya NO están montados. El montaje anterior fue temporal.
Antes accedimos a los recursos remotos, realizando un montaje de forma manual (comandos mount/umount). Si reiniciamos el equipo cliente, podremos ver que los montajes realizados de forma manual ya no están. Si queremos volver a acceder a los recursos remotos debemos repetir el proceso de montaje manual, a no ser que hagamos una configuración de montaje permanente o automática.

Para configurar acciones de montaje automáticos cada vez que se inicie el equipo, debemos configurar el fichero /etc/fstab. Veamos un ejemplo:
//IP-servidor-samba/public /mnt/remotoXX/public cifs username=soldado1,password=clave 0 0
Reiniciar el equipo y comprobar que se realiza el montaje automático al inicio.
Incluir contenido del fichero /etc/fstab en la entrega.
