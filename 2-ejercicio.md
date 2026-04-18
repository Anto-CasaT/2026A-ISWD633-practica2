### Crear contenedor de Postgres sin que exponga los puertos. 
```
docker run -d --name srv-postgres -e POSTGRES_PASSWORD=1234 -e POSTGRES_USER=postgres postgres:alpine
```
<img width="1646" height="458" alt="image" src="https://github.com/user-attachments/assets/533950b7-8b01-4e40-9cd7-8a05a2b287f3" />

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d --name srv-pgadmin -p 8080:80 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_P
```
<img width="1697" height="687" alt="image" src="https://github.com/user-attachments/assets/7956195a-f43e-495c-ab5e-a637d0e8dab7" />

### Conectar ambos contenedores en la misma red
<img width="934" height="198" alt="image" src="https://github.com/user-attachments/assets/4df34a54-5696-48fe-86f4-279c6c10e312" />


La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 5432 

![Imagen](esquema-2-ejercicio.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
# COMPLETAR CON UNA CAPTURA DEL LOGIN
<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/5680f470-67f9-4e03-8987-5704b047d67a" />
<img width="1919" height="1130" alt="image" src="https://github.com/user-attachments/assets/ee44ee12-e42e-4ce9-a745-03e032c53e72" />


### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
<img width="1919" height="1109" alt="image" src="https://github.com/user-attachments/assets/f4a1870c-406c-4982-abfb-2251ed8bff3f" />



## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
<img width="985" height="381" alt="image" src="https://github.com/user-attachments/assets/7dacdd88-eb6a-4245-8dab-b0b974238718" />


