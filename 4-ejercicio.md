## Esquema para el ejercicio
![Imagen](esquema-4-ejercicio.PNG)

### Crear la red
```
docker network create net-wp -d bridge
```
<img width="944" height="83" alt="image" src="https://github.com/user-attachments/assets/c4702640-cc4e-494b-af33-d5d29e69be23" />

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -d --name srv-mysql8 --network net-wp -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wordpress -e MYSQL_PASSWORD=1234 mysql:8
```
<img width="1693" height="627" alt="image" src="https://github.com/user-attachments/assets/c109b02d-aa3f-49d3-bbc0-7dfbe36458bf" />


### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name srv-wordpress --network net-wp -p 9300:80 -e WORDPRESS_DB_HOST=srv-mysql8 -e WORDPRESS_DB_USER=wordpress -e WORDPRESS_DB_PASSWORD=1234 -e WORDPRESS_DB_NAME=wordpress wordpress
```
<img width="1694" height="906" alt="image" src="https://github.com/user-attachments/assets/34f0141a-716b-4195-93d9-9ca906f6bfc5" />


De acuerdo con el trabajo realizado, en el esquema del ejercicio el puerto a es **9300**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
# COLOCAR UNA CAPTURA DE LA CONFIGURACIÓN
<img width="1600" height="947" alt="image" src="https://github.com/user-attachments/assets/1652b229-3f17-40d8-9f81-8906d2f797cb" />
<img width="1909" height="988" alt="image" src="https://github.com/user-attachments/assets/f8e3971f-4955-4f3e-815e-246d99bc4494" />


Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
<img width="1430" height="840" alt="image" src="https://github.com/user-attachments/assets/555b38a3-517a-4147-8a38-9eae72a79642" />
<img width="1919" height="1103" alt="Captura de pantalla 2026-04-19 212236" src="https://github.com/user-attachments/assets/b3803452-bcc0-402b-9d16-75d978944f8c" />

# COLOCAR UNA CAPTURA DEL SITO EN DONDE SEA VISIBLE LA PUBLICACIÓN.
<img width="959" height="559" alt="image" src="https://github.com/user-attachments/assets/1548b56c-6134-4ee3-b7be-a92a068e613a" />

### Eliminar el contenedor wordpress
```
docker rm -f srv-wordpress
```
<img width="615" height="132" alt="image" src="https://github.com/user-attachments/assets/3cb3d17f-f134-4aa8-8087-ef0f543f8788" />


### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
```
docker run -d --name srv-wordpress --network net-wp -p 9300:80 -e WORDPRESS_DB_HOST=srv-mysql8 -e WORDPRESS_DB_USER=wordpress -e WORDPRESS_DB_PASSWORD=1234 -e WORDPRESS_DB_NAME=wordpress wordpress
```
<img width="1699" height="108" alt="image" src="https://github.com/user-attachments/assets/a7f50770-1314-4c13-b0ee-bf1e106e5d63" />


### ¿Qué ha sucedido, qué puede observar?
El sitio WordPress sigue funcionando correctamente con todos los datos, 
tema y publicaciones intactas. Esto ocurre porque los datos están 
almacenados en el contenedor MySQL (srv-mysql8) y no en el contenedor 
WordPress. Al recrear el contenedor WordPress, este se reconecta a la 
misma base de datos recuperando toda la información.
<img width="1919" height="1157" alt="image" src="https://github.com/user-attachments/assets/3ee92251-a47c-4327-9786-e544ec044544" />

