#  Cliente para autenticacion LDAP

- ip de casa:
  - server06g: 192.168.0.91
  - client06g: 192.168.0.92
- ip de clase:
  - server06g: 172.19.6.31
  - client06g: 172.19.6.32

## 1. Preparativos

- Ir a MV cliente.
  - nmap -Pn IP-LDAP-SERVERXX | grep -P '389|636', para comprobar que el servidor LDAP es accesible desde la MV2 cliente.

   ![1.1]()

  - ldapsearch -H ldap://IP-LDAP-SERVERXX:389 -W -D "cn=Directory Manager" -b "dc=ldapXX,dc=curso2021" "(uid=*)" | grep dn, comprobamos que los usuarios del LDAP remoto son visibles en el cliente.

   ![1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Autenticacion-con-389-DS/img/Captura%20de%20pantalla_2020-11-30_09-05-26.png?raw=true)

## 2. Configurar autenticación LDAP

###  2.1 Crear conexión con servidor
  - Ir a la MV cliente.
  - No aseguramos de tener bien el nombre del equipo y nombre de dominio (/etc/hostname, /etc/hosts)
  - Ir a Yast -> Cliente LDAP y Kerberos.
  - Configurar como la imagen de ejemplo:
    - BaseDN: dc=ldapXX,dc=curso2021
    - DN de usuario: cn=Directory Manager
    - Contraseña: CLAVE del usuario cn=Directory Manager.

    ![2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Autenticacion-con-389-DS/img/Captura%20de%20pantalla_2020-11-30_08-51-22.png?raw=true)

  - Al final usar la opción de Probar conexión

    ![2.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Autenticacion-con-389-DS/img/Captura%20de%20pantalla_2020-11-30_08-51-33.png?raw=true)


### 2.2 Comprobar con comandos

  - Vamos a la consola con usuario root, y probamos lo siguiente:
  - id mazinger
  - su -l mazinger # Entramos con el usuario definido en LDAP
  - getent passwd mazinger # Comprobamos los datos del usuario
  - cat /etc/passwd | grep mazinger # El usuario NO es local

    ![2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Autenticacion-con-389-DS/img/Captura%20de%20pantalla_2020-11-30_09-04-28.png?raw=true)
