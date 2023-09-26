# docker-volumenes

Trabajando con volúmenes docker

Descargar imagen httpd y comprobar que está en equipo.

Para instalar la imagen httpd en el PC hay que usar este comando:

docker pull httpd

Para saber si está descargado usaremos en comando:

docker image list

Crear contenedor asir_httpd y mapear el puerto 80 del contenedor con el puerto 8000 de la máquina.

Con este simple comando ya crearemos el contenedor asir_httpd y ya lo mapeamos con los puertos correspondientes de la práctica.

docker run -dit --name asir_httpd -p 8000:80 httpd

Utiliza bind mount para que el directorio apache2 esté montado en el directorio que tu elijas.

Para hacer esto, hay que implementar al comando anterior esta línea:

-v “$PWD”/htdocs:/usr/local/apache2/htdocs

En mi caso voy a redirigirlo al directorio de apache que tenía ya creado.

Haz un “hello world” y comprueba que funciona en el navegador.

Vamos a localhost:8000 y comprobamos que el “hello world” está en la página, que en mi caso como lo hice en un html muy simple, pues sale de forma simple.

Cambia el nombre del contenedor a 'asir_web1'.
Como no se puede cambiar el nombre tras haber creado el contenedor, creamos un contenedor nuevo con el nombre cambiado y con las mismas características.
docker run -dit --name asir_web1 -p 8000:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4


Crear un contenedor con el mismo directorio pero con distinto puerto.
Ahora crearemos el contenedor asir_web2 con la misma ruta de directorios pero con el puerto num 9080. Utilizaremos este comando:
docker run -dit --name asir_web2 -p 9080:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:2.4


Comprobar que los dos contenedores sirven cuando buscas con el localhost.
Ahora si ponemos tanto el localhost 8000 como el 9080 nos va a aparecer lo mismo, ya que lo tenemos apuntando los dos al mismo directorio.
