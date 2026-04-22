# BIND MOUNT

En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen>
```

ó

```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```

- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.

### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.

![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)

![Volúmenes](volumen-host.PNG)

# COMPLETAR CON EL COMANDO

docker run -d --name mi_nginx -P -v "$(pwd)/nginx/html:/usr/share/nginx/html" nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Al ingresar, se muestra un error de tipo "403 Forbidden" (o la página no se encuentra). Esto ocurre porque la carpeta local `html` que hemos montado hacia el contenedor está completamente vacía y sobreescribe (u oculta) lo que estaba por defecto en ella.

### ¿Qué pasa con el archivo index.html del contenedor?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

El archivo `index.html` original de Nginx que venía con el contenedor queda subyacente o temporalmente inaccesible. El directorio del host domina sobre su comportamiento al usar un bind mount.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html

### ¿Qué sucede al ingresar al servidor de nginx?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

El archivo `index.html` original de Nginx que venía con el contenedor queda subyacente o temporalmente inaccesible. El directorio del host domina sobre su comportamiento al usar un bind mount.

### Eliminar el contenedor

# COMPLETAR CON EL COMANDO

docker rm -f mi_nginx

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

El nuevo contenedor mostrará el sitio web del template, lo que demuestra claramente que los datos persisten, se mantienen en el disco de nuestro host propio e independiente del ciclo de vida que tengan los contenedores asociados a él.
