# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

Consultar: Cómo se gestionan datos confidenciales con los secretos de Docker (Docker Secrets).
# Mi Aprendizaje

- Aprendí que `docker pull` descarga imágenes y que sin tag se usa `latest` por defecto.
- Aprendí que el ID de las imágenes se genera con **SHA256**, visible con `docker inspect`.
- Aprendí que `docker run -d` ejecuta contenedores en segundo plano.
- Aprendí que el mapeo de puertos debe especificarse al crear el contenedor, no después.
- Aprendí que MySQL y PostgreSQL requieren variables de entorno obligatorias para funcionar.
- Aprendí que las redes bridge permiten comunicación entre contenedores.
- Aprendí que los datos persisten en la BD aunque se elimine el contenedor de la aplicación.
- En Windows, `grep` no está disponible, se usa `findstr` como alternativa.

## Docker Secrets

Docker Secrets es un mecanismo para gestionar datos confidenciales como 
contraseñas, tokens o claves API de forma segura, evitando exponerlos 
como variables de entorno en texto plano.

- Los secretos se almacenan cifrados en el gestor de Docker (Swarm).
- Solo los contenedores autorizados pueden acceder a ellos.
- Se crean con: `docker secret create <nombre> <archivo>`
- Se usan en servicios con: `--secret <nombre>`
- Los secretos se montan en `/run/secrets/<nombre>` dentro del contenedor.
