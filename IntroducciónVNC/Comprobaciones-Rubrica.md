#  Introducción-VNC

## Comprobaciones Para Rúbrica:

`` Nota: Esto se realizó en el PC de casa, por lo tanto he tenido que cambiar la IP de cada maquina virtual.``

``
192.168.0.17 = Windows Slave VNC. 192.168.0.16 = Windows Master VNC.
192.168.0.31 = OpenSUSE Slave VNC
192.168.0.32 = OpenSUSE Master VNC
``

### (2.1) Comprobaciones finales
- Para verificar que se han establecido las conexiones remotas:



- Ir al servidor VNC y usar el comando _netstat -n_ para ver las conexiones VNC con el cliente.

- Conectar desde Window Master hacia el Windows Slave.

![2.1.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Introducci%C3%B3nVNC/img/2.1.1.PNG?raw=true)

- Conectar desde GNU/Linux Master hacia el Windows Slave.

![2.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Introducci%C3%B3nVNC/img/2.1.2.PNG?raw=true)

### (4.1) Comprobaciones finales
- Comprobaciones para verificar que se han establecido las conexiones remotas:

- Conectar desde GNU/Linux Master hacia GNU/Linux Slave.

- Ejecutar _lsof -i -n_ en el servidor para comprobar las conexiones VNC.

- Ejecutar _vncserver -list_ en el servidor.


![4.1.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Introducci%C3%B3nVNC/img/4.1.1.PNG?raw=true)

- Conectar desde Window Master hacia GNU/Linux Slave.
- Ejecutar _lsof -i -n_ en el servidor para comprobar las conexiones VNC.

- Ejecutar _vncserver -list_ en el servidor.

![4.1.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Introducci%C3%B3nVNC/img/4.1.2.PNG?raw=true)
