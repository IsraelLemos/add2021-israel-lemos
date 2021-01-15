## Vagrant con Virtualbox

### 3.3 Comprobar
Vamos a crear una MV nueva y la vamos a iniciar usando Vagrant:

- Debemos estar dentro de vagrantXX-celtics.
- vagrant up, para iniciar una nueva instancia de la máquina.

  ![3.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-32-03.png?raw=true)

- vagrant ssh: Conectar/entrar en nuestra máquina virtual usando SSH.

 ![3.3.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-33-01.png?raw=true)


### 5.2 Comprobar
Para confirmar que hay un servicio a la escucha en 4567, desde la máquina real podemos ejecutar los siguientes comandos:

- En el HOST-CON-VAGRANT (Máquina real). Comprobaremos que el puerto 4567 está a la escucha.
- _vagrant port_ para ver la redirección de puertos de la máquina Vagrant.

 ![5.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-47-34.png?raw=true)

- En HOST-CON-VAGRANT, abrimos el navegador web con el URL http://127.0.0.1:4567. En realidad estamos accediendo al puerto 80 de nuestro sistema virtualizado.

 ![5.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-48-57.png?raw=true)


### 6.1 Proyecto Lakers (Suministro mediante shell script)
Ahora vamos a suministrar a la MV un pequeño script para instalar Apache.

Crear directorio vagrantXX-lakers para nuestro proyecto.
Entrar en dicha carpeta.
Crear la carpeta html y crear fichero html/index.html con el siguiente contenido:

![6.1.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-59-30.png?raw=true)

![6.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-42-55.png?raw=true)


![6.1.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-58-43.png?raw=true)

Incluir en el fichero de configuración Vagrantfile lo siguiente:

 ![6.1.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_08-57-54.png?raw=true)

 ![6.1.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-06-46.png?raw=true)

Para verificar que efectivamente el servidor Apache ha sido instalado e iniciado, abrimos navegador en la máquina real con URL http://127.0.0.1:4567.

 ![6.1.6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-41-32.png?raw=true)

### 6.2 Proyecto Raptors (Suministro mediante Puppet)

Se pide hacer lo siguiente.

Crear directorio vagrantXX-raptors como nuevo proyecto Vagrant.
Modificar el archivo Vagrantfile de la siguiente forma:

![6.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-23-08.png?raw=true)

![6.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-23-54.png?raw=true)

Cuando usamos config.vm.provision "shell", inline: '"echo "Hola"', se ejecuta directamente el comando especificado en la MV. Es lo que llamaremos provisión inline.

Crear la carpeta manifests. OJO: un error muy típico es olvidarnos de la "s" final.
Crear el fichero manifests/nombre-del-alumnoXX.pp, con las órdenes/instrucciones Puppet necesarias para instalar el software que elijamos (Cambiar PACKAGENAME por el paquete que queramos).

 Ejemplo:
package { 'PACKAGENAME':
  ensure => 'present',
}

![6.2.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-26-22.png?raw=true)

![6.2.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_09-51-10.png?raw=true)

Para que se apliquen los cambios de configuración tenemos 2 caminos:

Con la MV encendida
- vagrant reload, recargar la configuración.
![6.2.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_10-19-09.png?raw=true)

- vagrant provision, volver a ejecutar la provisión.
![6.2.6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_10-19-49.png?raw=true)


### 7.2 Crear caja Vagrant
Una vez hemos preparado la máquina virtual ya podemos crear el box.

Vamos a crear una nueva carpeta vagrantXX-bulls, para este nuevo proyecto vagrant.

![7.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_10-11-53.png?raw=true)

VBoxManage list vms, comando de VirtualBox que muestra los nombres de nuestras MVs. Elegir una de las máquinas (VMNAME).

![7.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_10-11-31.png?raw=true)

Nos aseguramos que la MV de VirtualBox VMNAME está apagada.
- _vagrant package --base VMNAME --output nombre-alumnoXX.box_ , parar crear nuestra propia caja.

![7.2.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-14_10-32-53.png?raw=true)


Comprobamos que se ha creado el fichero nombre-alumnoXX.box en el directorio donde hemos ejecutado el comando.

- _vagrant box add nombre-alumno/bulls nombre-alumnoXX.box_ , añadimos la nueva caja creada por nosotros, al repositorio local de cajas vagrant de nuestra máquina.

![7.2.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-18_10-21-53.png?raw=true)

![7.2.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-18_10-22-37.png?raw=true)

- _vagrant box list_, consultar ahora la lista de cajas Vagrant disponibles.

![7.2.6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Vagrant-con-Virtualbox/img/Captura%20de%20pantalla_2020-12-18_10-22-56.png?raw=true)
