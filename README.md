# PrestaShop con Docker Compose

Este proyecto utiliza **Docker Compose** para levantar tres servicios: **MySQL**, **PrestaShop** y **phpMyAdmin**. A continuación se explica brevemente cómo configurarlos y ejecutarlos.

## Estructura del Proyecto

- `docker-compose.yml`: Define los servicios de **MySQL**, **PrestaShop** y **phpMyAdmin**.
- `.env`: Contiene las variables de entorno para configurar los servicios.

## Servicios

### 1. **MySQL**
- **Imagen**: `mysql:latest`
- **Puertos**: 3306
- **Volumen**: `Mysql_data` (persistencia de datos)
- **Variables**: Configura la base de datos de PrestaShop.

### 2. **PrestaShop**
- **Imagen**: `prestashop/prestashop:latest`
- **Puertos**: 8080
- **Volumen**: `Prestashop` (persistencia de archivos)
- **Dependencia**: Depende de MySQL (se inicia cuando MySQL está saludable).

### 3. **phpMyAdmin**
- **Imagen**: `phpmyadmin/phpmyadmin:latest`
- **Puertos**: 8081
- **Dependencia**: Depende de MySQL (se inicia cuando MySQL está saludable).

## Volúmenes

- `Mysql_data`: Almacena los datos de la base de datos.
- `Prestashop`: Almacena los archivos de PrestaShop.

## Variables de Entorno

El archivo `.env` contiene las siguientes variables:

```dotenv
# MySQL
MYSQL_ROOT_PASSWORD=admin
MYSQL_DATABASE=prestashop
MYSQL_USER=admin
MYSQL_PASSWORD=admin

# PrestaShop
DB_SERVER=mysql
DB_NAME=prestashop
DB_USER=admin
DB_PASSWD=admin
PS_INSTALL_AUTO=1
PS_LANGUAGE=es
PS_COUNTRY=es
PS_FOLDER_ADMIN=admin45

# phpMyAdmin
PMA_HOST=mysql
PMA_PORT=3306
