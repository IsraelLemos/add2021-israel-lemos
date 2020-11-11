# Servidor impresión Windows

- Nota:
  - Ip de casa-> 192.168.0.90=server06w
  - Ip de casa-> 192.168.0.91=client06w
  - Ip de clase-> 172.19.6.=server06w
  - Ip de clase-> 172.19.6.=client06w

## 1.3 Probar la impresora en local
Para crear un archivo PDF no hará falta que cambies la aplicación que estés usando, simplemente ve a la opción de imprimir y selecciona "Impresora PDF", en segundos tendrás creado tu archivo PDF.

Puedes probar la nueva impresora abriendo el Bloc de notas y creando un fichero luego selecciona imprimir. Cuando finalice el proceso se abrirá un fichero PDF con el resultado de la impresión.

- Probar la impresora remota imprimiendo documento imprimirXXs-local.

  ![1.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-4.PNG?raw=true)

  ![1.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-5.PNG?raw=true)

  ![1.3.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-6.PNG?raw=true)

  ![1.3.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-7.PNG?raw=true)



## 2.2 Comprobar desde el cliente
Vamos al cliente:

- Buscar recursos de red del servidor. Si tarda en aparecer ponemo  _\\ip-del-servidor_ en la barra de navegación.

 ![2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura%20de%20pantalla_2020-11-06_10-35-08.png?raw=true)
- Seleccionar impresora -> botón derecho -> conectar.

 ![2.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura%20de%20pantalla_2020-11-06_10-35-40.png?raw=true)

 ![2.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura%20de%20pantalla_2020-11-06_10-36-10.png?raw=true
)

  - Ponemos usuario/clave del Windows Server.
- Ya tenemos la impresora remota configurada en el cliente.
- Probar la impresora remota imprimiendo documento _imprimirXXw-remoto_.

 ![2.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura.PNG?raw=true)

 ![2.2.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-2.PNG?raw=true)

 ![2.2.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-12.PNG?raw=true)

## 3.3 Comprobar desde el navegador

Vamos a realizar seguidamente una prueba sencilla en tu impresora de red:

- Accede a la configuración de la impresora a través del navegador.

 ![3.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura%20de%20pantalla_2020-11-10_12-20-36.png?raw=true)

- Poner en pausa los trabajos de impresión de la impresora.

 ![3.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura%20de%20pantalla_2020-11-10_12-21-34.png?raw=true)

 ![3.3.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-1.PNG?raw=true)



- Ir a MV cliente.
- Probar la impresora remota imprimiendo documento imprimirXXw-web.

  ![3.3.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-10.PNG?raw=true)

  ![3.3.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-11.PNG?raw=true)

  ![3.3.7](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-13.PNG?raw=true)

  - Comprobar que al estar la impresora en pausa, el trabajo aparece en cola de impresión.

  ![3.3.6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-8.PNG?raw=true)

- Finalmente pulsa en reanudar el trabajo para que tu documento se convierta a PDF.

 ![3.3.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura-9.PNG?raw=true)

 ![3.3.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Servidor-de-impresion-Windows/img/Captura%20de%20pantalla_2020-11-10_12-21-34.png?raw=true)
