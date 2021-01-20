## Docker

### 3.2 Comprobar

- Abrimos una nueva terminal.
docker ps, nos muestra los contenedores en ejecución.Podemos apreciar que la última columna nos indica que el puerto 80 del contenedor está redireccionado a un puerto local 0.0.0.0.:PORT -> 80/tcp.

 ![3.2.1]()


- Abrir navegador web y poner URL 0.0.0.0.:PORT. De esta forma nos conectaremos con el servidor Nginx que se está ejecutando dentro del contenedor.
 ![3.2.2]()

- Comprobar el acceso a holamundo1.html.
 ![3.2.3]()
Paramos el contenedor app2nginx1 y lo eliminamos.
