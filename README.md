# Para versiones de  inferiores a 1.7.8
Parra versiones suepriores ir este repositorio ->

1. Descarga la versión que quieras lanzar (máximo 1.7.7.8) desde la web oficial: https://prestashop.com/versions/
2. Coloca el fichero zip en este directorio
3. Renombarlo por `prestashop.zip`.
4. Ejectuar este comando.

```bash
  unzip prestashop.zip -d html && \
  docker compose up -d
```
 >  Si tenemos algun problema hacerlo a mano:
> 1. Descomprimir el fichero prestashop.zip en una carpeta llamada html
  > 2. Lanzar el comando `docker compose up -d`

5. Acceder a http://localhost:8001/ y seguir los pasos de instalación de prestashop

Nos alertara de que hay versiones nuevas, le decimos que no gracias 🙃. 
Entiendo que si quieres la última version en el paso 1 habrías seleccionado esa.

6. Eliminar la carpeta install de html
```bash
    rm -rf html/install
```

Los datos de conexión a la base de datos los tienes en .env por si quieres cambiarlos, lo de por defecto son:
> - **DB_SERVER**: mysql
> - **DB_USER**: root
> - **DB_PASS**: prestashop
> - **DB_NAME**: prestashop

Para lanzar una vez instalado
---
```bash
docker compose up -d
```

```bash
unzip prestashop.zip -d html 
```

**Para reconstruir**
```bash
docker compose down -v
docker compose build --no-cache
docker compose up --build --force-recreate
```

Si queremos volver a instalar eliminar la carpeta html y volver al paso 4.

Para cambiar el directorio de admin
1. Renombrar el Directorio adminsdadadwef por el que queramos
2. Actualizar la configuración en `config/settings.inc.php`, buscar `define('_PS_ADMIN_DIR_' ...` y cambiar el valor por el nuevo nombre del directorio.
3. Borrar cache