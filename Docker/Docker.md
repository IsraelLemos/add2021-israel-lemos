## Docker

### 3.2 Comprobar

- Abrimos una nueva terminal.
docker ps, nos muestra los contenedores en ejecución.Podemos apreciar que la última columna nos indica que el puerto 80 del contenedor está redireccionado a un puerto local 0.0.0.0.:PORT -> 80/tcp.

 ![3.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-11_10-40-33.png?raw=true)


- Abrir navegador web y poner URL 0.0.0.0.:PORT. De esta forma nos conectaremos con el servidor Nginx que se está ejecutando dentro del contenedor.
 ![3.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-11_10-39-34.png?raw=true)

- Comprobar el acceso a holamundo1.html.
 ![3.2.3]()
Paramos el contenedor app2nginx1 y lo eliminamos.



### 3.3 Migrar la imagen a otra máquina


- Exportar imagen Docker a fichero tar:
 - docker save -o alumnoXXdocker.tar nombre-alumno/nginx1, guardamos la imagen "nombre-alumno/nginx1" en un fichero tar.


  ![3.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-02-02.png?raw=true)

### 4.2 Crear imagen a partir del Dockerfile

El fichero Dockerfile contiene toda la información necesaria para construir el contenedor, veamos:

- cd dockerXXa, entramos al directorio con el Dockerfile.
- docker build -t nombre-alumno/nginx2 .
- docker images, ahora debe aparecer nuestra nueva imagen.
