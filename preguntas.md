# Ejercicio 1
Capacitación: Git, bash y docker
**Integrantes:**
- Joan Tasayco
- Angello Peña
- Carlos Gomez

**1. ¿Qué es y para qué sirve GIT?**
Es una herramienta de control de versiones, que nos permite respaldar nuestro trabajo, compoartirlo y controlar sus cambios.

**2. ¿Que es Github o bitbucket?**
Son repositorios de codigo que nos puede brindar una cuenta libre con sus limitaciones

**3. ¿Qué es y para qué sirve el SSH?**
ssh SH o Secure Shell, es un protocolo de administración remota que permite a los usuarios controlar y modificar sus servidores remotos a través de Internet.

**4. ¿Que pasa si cambio de PC? ¿Tendré que generar el SSH nuevamente?¿Por qué?**
Si hay que generar un nuevo SSH, por que cada key es unico por pc

**5. ¿Qué es markdown? ¿Para qué sirve?**
Markdown es un lenguaje de marcado que facilita la aplicación de formato a un texto empleando una serie de caracteres de una forma especial

**6. ¿Cómo inicializo y configuro un proyecto de git?**
con el comando git init

# Parte 5

## 1. Listar las carpetas que hay dentro de la imagen

- Levantar la imagen: docker run -d -p "8080:80" --name  Mikhael -t angello/orbis-training-docker:0.2.0 bash
- Se acceder a la imagen: docker run -d -p "8080:80" --name  Mikhael -t angello/orbis-training-docker:0.2.0 bash
- Se lista: ls -la

### ¿Porqué es necesario crear un contenedor con esta bandera -it ? ¿Qué pasa si no le pongo -it?
La bandera -it especifica que se cree en modo interactivo y usar el TTY, si no se pone sale error de #PATH

### ¿Para qué sirve ejecutar el comando bash al ejecutar una imagen?
Permite activar el bash para ejecutar comandos sobre la imagen

## 2. En caso de que el contenedor esté, entonces eliminarlo
docker kill Mikhael

### ¿Cuál es la diferencia entre docker ps y docker ps -a?
docker ps, lista los procesos ejecutando. 
docker ps -a, lista todos los procesos.

## 3. Copiar el archivo preguntas.md en la imagen
from node:10.10.0-slim
label maintainer = 'williams.pena@orbis.com.pe'
run apt-get update && apt-get install
copy preguntas.md  ./app/
expose 80

## 4. Verificar que el archivo preguntas.md exista en la imagen

- Crear en modo interactivo: docker run -i angello/orbis-training-docker:0.2.0 bash
- Obtener el id de la instancia: docker inspect -f '{{.Id}}'  Mikhael | resultado: fe1169425bbb4711915cf15e2f68e6e105f478385bebbfea14cfc9408cdd3536

--Ubicacion del proyecto desde ubuntus: 
/mnt/d/angello/proyectos/orbis-training-project

## 5. Subir los cambios como un nuevo feature
git commit -m 'feat preguntas: Se agrega parte de las respuestas de la Parte 5'

## 6. Al construir la imagen, listar los archivos del directorio /app
docker run --name Mikhael -i angello/orbis-training-docker:0.2.0 ls /app

## 7. Adicionalmente, al construir la imagen, mostrar el contenido del archivo preguntas.md
from node:10.10.0-slim
label maintainer = 'williams.pena@orbis.com.pe'
copy preguntas.md  ./app/
run apt-get update && apt-get install && cat app/preguntas.md
expose 80

## 8. Agregar el comando para ejecutar el contenedor
docker run --name Mikhael -i -t angello/orbis-training-docker:0.2.0 cat app/preguntas.md

## 9. Subir los cambios como un nuevo feature
git commit -m 'feat: Se agrega respuestas restantas de la parte 5'
git tag -a v1.1

## Preguntas

1. ¿Cuál es la diferencia entre una imagen y un contenedor?
La imagen son un conjunto de archios que representa un aplicacion o conjuno de aplicaciones, el conteneder es el espacio de memoria sobre el cual se ejecuta la imagene.

2. ¿Cómo listo las imágenes que hay en mi computadora?
docker images

3. ¿Cómo salgo de un contenedor de docker?
exit

4. ¿Se elimina el contenedor al salir de ella?
Si estea creado de modo interactivo

5. ¿Cómo elimino un contenedor?
docker rm idcontenedor

6. ¿Para qué es necesario el flag `-i`, `-t`, `--rm`?
-i: ejecuta el contenedor de modo interactivo
-t: actiua uso de la terminal tty
--rm: automaticamente eliminara el contenedor cuando se salga

7. ¿Cómo verifico que el archivo creado se encuentra en la imagen?
ejecutando la imagen eun contenedor y listarlo
docker run --name Mikhael -i angello/orbis-training-docker:0.2.0 ls /app

8. ¿Cómo se comenta una linea de código en Dockerfile?
con el caracter #