# Mi Aprendizaje - Práctica 3

En esta práctica, he consolidado conocimientos importantes sobre la gestión de contenedores:

1. **Persistencia de datos:** Comprendí las diferencias clave entre *bind mounts* y *volúmenes nombrados*, viendo en la práctica cómo los volúmenes son ideales y más seguros para asegurar que la información de bases de datos y CMS no se pierda al borrar los contenedores.
2. **Redes con Docker:** Aprendí a usar redes *bridge* definidas por el usuario. Al conectar el servidor de Drupal, el cliente `pgadmin4` y la base de datos a `net-drupal`, pude realizar la conexión utilizando simplemente el nombre del contenedor (`server-postgres`) sin preocuparme por las IPs.
3. **Resolución de errores de versiones:** Aprendí que usar la etiqueta `latest` en imágenes oficiales como Postgres puede generar problemas inesperados debido a actualizaciones de versiones mayores (de 16/17 a 18). El problema del montaje de datos de postgres 18 se solucionó especificando una versión LTS (`postgres:16`), lo cual me enseñó la importancia de dejar en firme (fijar) las versiones en entornos de producción.
