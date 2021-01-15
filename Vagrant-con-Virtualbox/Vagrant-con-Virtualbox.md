## Vagrant con Virtualbox

### 3.3 Comprobar
Vamos a crear una MV nueva y la vamos a iniciar usando Vagrant:

Debemos estar dentro de vagrantXX-celtics.
vagrant up, para iniciar una nueva instancia de la máquina.
vagrant ssh: Conectar/entrar en nuestra máquina virtual usando SSH.


### 5.2 Comprobar
Para confirmar que hay un servicio a la escucha en 4567, desde la máquina real podemos ejecutar los siguientes comandos:

En el HOST-CON-VAGRANT (Máquina real). Comprobaremos que el puerto 4567 está a la escucha.
vagrant port para ver la redirección de puertos de la máquina Vagrant.
En HOST-CON-VAGRANT, abrimos el navegador web con el URL http://127.0.0.1:4567. En realidad estamos accediendo al puerto 80 de nuestro sistema virtualizado.


### 6.1 Proyecto Lakers (Suministro mediante shell script)
Ahora vamos a suministrar a la MV un pequeño script para instalar Apache.

Crear directorio vagrantXX-lakers para nuestro proyecto.
Entrar en dicha carpeta.
Crear la carpeta html y crear fichero html/index.html con el siguiente contenido:

Proyecto Lakers
<p>Curso202021</p>
<p>Nombre-del-alumno</p>
Crear el script install_apache.sh, dentro del proyecto con el siguiente contenido:
#!/usr/bin/env bash

apt-get update
apt-get install -y apache2
Incluir en el fichero de configuración Vagrantfile lo siguiente:

config.vm.hostname = "nombre-alumnoXX-lakers"
config.vm.provision :shell, :path => "install_apache.sh", para indicar a Vagrant que debe ejecutar el script install_apache.sh dentro del entorno virtual.
config.vm.synced_folder "html", "/var/www/html", para sincronizar la carpeta exterior html con la carpeta interior. De esta forma el fichero "index.html" será visible dentro de la MV.
vagrant up, para crear la MV.
Podremos notar, al iniciar la máquina, que en los mensajes de salida se muestran mensajes que indican cómo se va instalando el paquete de Apache que indicamos.
Para verificar que efectivamente el servidor Apache ha sido instalado e iniciado, abrimos navegador en la máquina real con URL http://127.0.0.1:4567.


### 6.2 Proyecto Raptors (Suministro mediante Puppet)
Enlace de interés:

Crear un entorno de desarrollo con vagrant y puppet
friendsofvagrant.github.io -> Puppet Provisioning
Veamos imágenes de ejemplo (de Aarón Gonźalez Díaz) con Vagrantfile configurado con puppet:

vagranfile-puppet

Fichero de configuración de puppet mipuppet.pp:

vagran-puppet-pp-file

Se pide hacer lo siguiente.

Crear directorio vagrantXX-raptors como nuevo proyecto Vagrant.
Modificar el archivo Vagrantfile de la siguiente forma:
Vagrant.configure("2") do |config|
  ...
  config.vm.hostname = "nombre-alumnoXX-raptors"
  ...
  # Nos aseguramos de tener Puppet en la MV antes de usarlo.
  config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y puppet"

  # Hacemos aprovisionamiento con Puppet
  config.vm.provision "puppet" do |puppet|
    puppet.manifest_file = "nombre-del-alumnoXX.pp"
  end
 end
Cuando usamos config.vm.provision "shell", inline: '"echo "Hola"', se ejecuta directamente el comando especificado en la MV. Es lo que llamaremos provisión inline.

Crear la carpeta manifests. OJO: un error muy típico es olvidarnos de la "s" final.
Crear el fichero manifests/nombre-del-alumnoXX.pp, con las órdenes/instrucciones Puppet necesarias para instalar el software que elijamos (Cambiar PACKAGENAME por el paquete que queramos). Ejemplo:
package { 'PACKAGENAME':
  ensure => 'present',
}
NOTA:

El Puppet es un gestor de infraestructura que veremos en profundidad otra actividad.
Podemos hacer el suministro con otros gestores de infraestructura como Salt-stack. Consultar enlace Salt Provisioner.
Para que se apliquen los cambios de configuración tenemos 2 caminos:

Con la MV encendida
vagrant reload, recargar la configuración.
vagrant provision, volver a ejecutar la provisión.
Con la MV apagada:
vagrant destroy, destruir la MV.
vagrant up volver a crearla.

### 7.2 Crear caja Vagrant
Una vez hemos preparado la máquina virtual ya podemos crear el box.

Vamos a crear una nueva carpeta vagrantXX-bulls, para este nuevo proyecto vagrant.
VBoxManage list vms, comando de VirtualBox que muestra los nombres de nuestras MVs. Elegir una de las máquinas (VMNAME).
Nos aseguramos que la MV de VirtualBox VMNAME está apagada.
vagrant package --base VMNAME --output nombre-alumnoXX.box, parar crear nuestra propia caja.
Comprobamos que se ha creado el fichero nombre-alumnoXX.box en el directorio donde hemos ejecutado el comando.
vagrant box add nombre-alumno/bulls nombre-alumnoXX.box, añadimos la nueva caja creada por nosotros, al repositorio local de cajas vagrant de nuestra máquina.
vagrant box list, consultar ahora la lista de cajas Vagrant disponibles.
