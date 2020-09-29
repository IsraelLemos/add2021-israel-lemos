# Comprobaciones Para Rúbrica:

## (2.1) Comprobaciones finales
- Para verificar que se han establecido las conexiones remotas:

- Conectar desde Window Master hacia el Windows Slave.
- Conectar desde GNU/Linux Master hacia el Windows Slave.
- Ir al servidor VNC y usar el comando _netstat -n_ para ver las conexiones VNC con el cliente.

`` Nota: Esto se realizo en el PC de casa, por lo tanto he tenido que cambiar la IP de cada maquina virtual a 192.168.0.17 para el Windows Server y 192.168.0.16 para el Windows Cliente ``

![2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Introducci%C3%B3nVNC/img/2.1.PNG?raw=true)


## (4.1) Comprobaciones finales
- Comprobaciones para verificar que se han establecido las conexiones remotas:

- Conectar desde Window Master hacia GNU/Linux Slave.
- Conectar desde Window Master hacia GNU/Linux Slave.
- Ejecutar _lsof -i -n_ en el servidor para comprobar las conexiones VNC.

![4.1.1](http://url/to/img.png)

- Ejecutar _vncserver -list_ en el servidor.

![4.1.2](http://url/to/img.png)
