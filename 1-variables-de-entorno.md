# Variables de Entorno
### ¿Qué son las variables de entorno?
Son pares clave-valor que se definen fuera del código de una aplicación y se utilizan para configurar el comportamiento de los programas en tiempo de ejecución, sin necesidad de modificar el código fuente.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

<img width="1279" height="86" alt="image" src="https://github.com/user-attachments/assets/6194beea-b9e8-4db2-b0aa-5c7b97839c69" />


# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

<img width="918" height="518" alt="image" src="https://github.com/user-attachments/assets/4368efe1-3c5e-45b4-a3e1-93d277ef7e01" />

### Crear un contenedor con la imagen de mysql, mapear todos los puertos
<img width="1128" height="566" alt="image" src="https://github.com/user-attachments/assets/05caf6d5-7b65-4edd-bb73-00c5c6e6576c" />


### ¿El contenedor se está ejecutando?
 No, porque MySQL requiere variables de entorno obligatorias
 <img width="786" height="66" alt="image" src="https://github.com/user-attachments/assets/06ed4507-e6a9-4315-9a78-53097b8a8974" />


### Identificar el problema
Los logs indican que se necesita especificar MYSQL_ROOT_PASSWORD, MYSQL_ALLOW_EMPTY_PASSWORD o MYSQL_RANDOM_ROOT_PASSWORD

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

### Solución
Crear el contenedor con -e MYSQL_ROOT_PASSWORD=1234
```
docker run -P -d --name srv-mysql -e MYSQL_ROOT_PASSWORD=1234 mysql
```
<img width="1378" height="182" alt="image" src="https://github.com/user-attachments/assets/bced19ec-62e6-4e8d-a746-bc14b21abf18" />


### ¿Qué bases de datos existen en el contenedor creado?
Las bases de datos que existen por defecto en el contenedor de MySQL son information_schema, mysql, performance_schema y sys.
<img width="912" height="602" alt="image" src="https://github.com/user-attachments/assets/a2272b08-48c0-430e-8597-5c34a71d60b2" />
