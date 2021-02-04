## Salt Stack

### 3.4 Comprobamos conectividad
  Desde el Máster comprobamos:

 - Conectividad hacia los Minions:
    - salt '*' test.ping
    - minionXXg:
    - True

![3.4.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-25_09-19-32.png?raw=true)


 - Versión de Salt instalada en los Minions:
    - salt '*' test.version
    - minionXXg:
    -  3000

![3.4.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-25_09-21-02.png?raw=true)


### 4.5 Aplicar el nuevo estado
Ir al Master:

- Consultar los estados en detalle y verificar que no hay errores en las definiciones.

  - salt '*' state.show_lowstate.

  ![4.5.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-25_09-37-50.png?raw=true)

  - salt '*' state.show_highstate.

  ![4.5.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-25_09-38-24.png?raw=true)

  - salt '*' state.apply apache, para aplicar el nuevo estado en todos los minions.
  ![4.5.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-25_09-39-47.png?raw=true)

### 5.1 Crear estado "users"

Vamos a crear un estado llamado users que nos servirá para crear un grupo y usuarios en las máquinas Minions (ver ejemplos en el ANEXO).

- Crear directorio /srv/salt/base/users.
- Crear fichero /srv/salt/base/users/init.sls con las definiciones para crear los siguiente:
  - Grupo mazingerz
  - Usuarios kojiXX, drinfiernoXX dentro de dicho grupo.

    ![5.1.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-29_10-30-34.png?raw=true)

    ![5.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-29_10-31-07.png?raw=true)


- Aplicar el estado.

  ![5.1.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-29_10-32-05.png?raw=true)



### 5.2 Crear estado "dirs"

Crear estado dirs para crear las carpetas private (700), public (755) y group (750) en el HOME del usuario koji (ver ejemplos en el ANEXO).

![5.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Salt-Stack/img/Captura%20de%20pantalla_2021-01-29_10-40-36.png?raw=true)




- Aplicar el estado dirs.
