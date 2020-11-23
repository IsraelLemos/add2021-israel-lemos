- Ip de casa: 192.168.0.91-> server06g
- Ip de casa: 192.168.0.62-> client06g

# DS por comandos

## 2.4 Comprobamos el acceso al contenido del LDAP

- _ldapsearch -b "dc=ldapXX,dc=curso2021" -x | grep dn_, muestra el contenido de nuestra base de datos LDAP. "dn" significa nombre distiguido, es un identificador que tiene cada nodo dentro del árbol LDAP.

 ![2.4.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura-4.PNG?raw=true)

- _ldapsearch -H ldap://localhost -b "dc=ldapXX,dc=curso2021" -W -D "cn=Directory Manager" | grep dn_, en este caso hacemos la consulta usando usuario/clave.

 ![2.4.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura%20de%20pantalla_2020-11-18_10-02-04.png?raw=true)


## 3.3 Comprobar el nuevo usuario
- _ldapsearch -W -D "cn=Directory Manager" -b "dc=ldapXX,dc=curso2021" "(uid=*)"_, para comprobar si se ha creado el usuario correctamente en el LDAP.

![3.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura%20de%20pantalla_2020-11-18_10-20-45.png?raw=true)
![3.3.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura%20de%20pantalla_2020-11-18_10-20-57.png?raw=true)


- Crear un archivo _mazinger-delete.ldif_ :
_dn: uid=mazinger,ou=people,dc=ldapXX,dc=curso2021
changetype: delete_

 ![3.3.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura-2.PNG?raw=true)



- Ejecutamos el siguiente comando para eliminar un usuario del árbol LDAP: _ldapmodify -x -D "cn=Directory Manager" -W -f mazinger-delete.ldif_

 ![3.3.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura-3.PNG?raw=true)


## 4.3 Comprobar los usuarios creados
- Ir a la MV cliente LDAP.
- _nmap -Pn IP-LDAP-SERVER_, comprobar que el puerto LDAP del servidor está abierto. Si no aparecen los puertos abiertos, entonces revisar el cortafuegos.

 ![4.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura-6.PNG?raw=true)


- _ldapsearch -H ldap://IP-LDAP-SERVER -W -D "cn=Directory Manager" -b "dc=ldapXX,dc=curso2021" "(uid=*)" | grep dn_ para consultar los usuarios LDAP que tenemos en el servicio de directorio remoto.

 ![4.3.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/DS-por-comandos/img/Captura-7.PNG?raw=true)
