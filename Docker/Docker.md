## Docker

### 3.2 Comprobar

- Abrimos una nueva terminal.
docker ps, nos muestra los contenedores en ejecución.Podemos apreciar que la última columna nos indica que el puerto 80 del contenedor está redireccionado a un puerto local 0.0.0.0.:PORT -> 80/tcp.

 ![3.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-11_10-40-33.png?raw=true)


- Abrir navegador web y poner URL 0.0.0.0.:PORT. De esta forma nos conectaremos con el servidor Nginx que se está ejecutando dentro del contenedor.
 ![3.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-11_10-39-34.png?raw=true)

- Comprobar el acceso a holamundo1.html.
 ![3.2.3]()



### 3.3 Migrar la imagen a otra máquina


- Exportar imagen Docker a fichero tar:
 - docker save -o alumnoXXdocker.tar nombre-alumno/nginx1, guardamos la imagen "nombre-alumno/nginx1" en un fichero tar.


  ![3.3.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-02-02.png?raw=true)

### 4.2 Crear imagen a partir del Dockerfile

El fichero Dockerfile contiene toda la información necesaria para construir el contenedor, veamos:

 ![4.2.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura-2.PNG?raw=true)

- cd dockerXXa, entramos al directorio con el Dockerfile.

 ![4.2.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-23-31.png?raw=true)

- docker build -t nombre-alumno/nginx2 .

 ![4.2.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-26-03.png?raw=true)


- docker images, ahora debe aparecer nuestra nueva imagen.

 ![4.2.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-36-54.png?raw=true)


### 4.3 Crear contenedor y comprobar

A continuación vamos a crear un contenedor con el nombre app4nginx2, a partir de la imagen nombre-alumno/nginx2. Probaremos con:

- docker run --name=app4nginx2 -p 8082:80 -t nombre-alumno/nginx2

![4.3.1]()

Desde otra terminal:
- docker ps, para comprobar que el contenedor está en ejecución y en escucha por el puerto deseado.

![4.3.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-39-53.png?raw=true)

- Comprobar en el navegador:
 - URL http://localhost:PORTNUMBER
  ![4.3.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-40-34.png?raw=true)
 - URL http://localhost:PORTNUMBER/holamundo2.html
  ![4.3.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-13_10-40-54.png?raw=true)

### 4.4 Usar imágenes ya creadas

  - Crea el directorio dockerXXb. Entrar al directorio.
   ![4.4.1](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-15_09-56-46.png?raw=true)

  - Crear fichero holamundo3.html con:
   - Proyecto: dockerXXb
   - Autor: Nombre del alumno
   - Fecha: Fecha actual


   ![4.4.2](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-15_10-00-09.png?raw=true)

  - Crea el siguiente Dockerfile

   ![4.4.3](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-15_10-02-44.png?raw=true)


  - docker build -t nombre-alumno/nginx3 ., crear la imagen.

  ![4.4.4](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-15_10-04-10.png?raw=true)

  - docker run --name=app5nginx3 -d -p 8083:80 nombre-alumno/nginx3, crear contenedor.

  ![4.4.5](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-15_10-05-16.png?raw=true)

  - Comprobar el acceso a "holamundo3.html".

  ![4.4.6](https://github.com/IsraelLemos/add2021-israel-lemos/blob/master/Docker/img/Captura%20de%20pantalla_2021-01-15_10-06-17.png?raw=true)
