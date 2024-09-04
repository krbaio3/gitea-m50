# gitea-m50

## Usar Docker para desplegar Gitea
Configuración básica de Docker Compose para levantar Gitea con una base de datos MySQL y almacenamiento persistente.

## Instrucciones para levantar Gitea:

Crea una carpeta para almacenar los datos de Gitea y la base de datos:
```bash

mkdir -p ~/gitea/{gitea-db,gitea}
cd ~/gitea
```

Guarda el archivo `docker-compose.yml` dentro de esta carpeta.
Levanta los servicios con Docker Compose:

```bash
docker-compose up -d
```

Accede a Gitea en http://localhost:3000 o el puerto que hayas configurado. 

En la primera ejecución, deberás completar la configuración inicial a través de la interfaz web.

### Explicación de la configuración:

- `gitea-db`: Contenedor que ejecuta la base de datos MariaDB para Gitea.
Se guarda en un volumen persistente para no perder los datos.
gitea: Contenedor que ejecuta Gitea.
- Se expone en el puerto 3000 para la interfaz web y el puerto 222 para las conexiones SSH a los repositorios.
- Las credenciales de base de datos se configuran mediante variables de entorno.

## Personalización:

Puedes cambiar las variables `MYSQL_ROOT_PASSWORD`, `MYSQL_USER`, `MYSQL_PASSWORD` y `MYSQL_DATABASE` según tus necesidades.
Para un entorno de producción, se considera usar un proxy reverso con HTTPS (por ejemplo, con `Nginx` o `Traefik`).
