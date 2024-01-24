## Pre-requisitos

Antes de comenzar, asegúrate de tener Docker y Docker Compose instalados en tu sistema. Visita [Docker](https://www.docker.com/get-started) y [Docker Compose](https://docs.docker.com/compose/install/) para las instrucciones de instalación.

## Clonar el Repositorio

Para obtener el proyecto junto con sus submódulos, ejecuta el siguiente comando en tu terminal:

```bash
git clone --recurse-submodules https://github.com/penti2s/project_combined_zapping.git
```
Si ya clonaste el repositorio sin los submódulos, puedes cargarlos con:


```
git submodule update --init --recursive
```


1 . Navega al directorio del proyecto clonado:
```
cd project_combined_zapping
```

2. Construye y levanta los contenedores con Docker Compose:
```
docker-compose up --build
```

3. Acceder a la Aplicación
Una vez que los contenedores estén corriendo, podrás acceder a la interfaz de usuario en:

```
http://localhost:3000
```
