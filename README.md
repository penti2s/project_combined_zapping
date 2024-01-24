# Zapping Streaming Service: Prueba Técnica

## Introducción y Desarrollo del Proyecto

Bienvenido al proyecto Zapping, una aventura técnica en el mundo la trasmicion de video. Mi enfoque inicial fue el backend, específicamente en Go. Comencé con la incógnita de cómo actualizar dinámicamente la playlist `.m3u8`, lo que se reveló como un desafío intrigante.

El primer paso fue desarrollar la lógica para actualizar la playlist, lo que implicó varias iteraciones hasta encontrar una solución satisfactoria. Inicialmente, abordé el problema de manera algo estática, asignando una duración fija de 10 segundos por fragmento. Sin embargo, pronto cambié este enfoque a uno más dinámico, basándome en la estructura principal de la playlist definida en sus primeras 4 líneas.

Usé estas líneas como base y, a partir de ahí, iteré sobre el archivo para agregar los segmentos necesarios. Cada tres segmentos, que equivalen a seis líneas, implementé una lógica para eliminar el primer elemento de la playlist, creando un efecto de bucle continuo. Además, enfrenté y resolví un problema donde el último segmento continuaba ejecutándose a pesar de que no había más fragmentos disponibles. La solución fue implementar una validación que reinicia la playlist desde el segmento 0 cuando esto sucede.

Posteriormente, me dediqué a desarrollar dos endpoints esenciales: uno para obtener la lista de reproducción y otro para los segmentos de video. Inicialmente, los creé en rutas separadas, pero luego descubrí que la biblioteca que estaba utilizando requería que ambos estuvieran en el mismo nivel.

Con el backend en su lugar, mi atención se dirigió al frontend. Decidí emplear una combinación de Vue 3, Nuxt 3 y DaisyUI para los estilos, buscando una solución más compleja y estructurada. Primero, creé las vistas para el streaming, los formularios de registro y login. Me concentré en la integración con la librería hls.js, asegurándome de que el componente correspondiente hiciera consultas periódicas para actualizar los segmentos y la playlist.

En el backend, desarrollé un sistema completo de autenticación, comenzando con la creación de un modelo de usuarios y la respectiva tabla en la base de datos. Implementé servicios para facilitar la conexión a la base de datos, creando endpoints para el registro, login y obtención de información del usuario. La seguridad fue una prioridad, por lo que las contraseñas se almacenan encriptadas con un salt. Para la autenticación, utilicé JWT, lo que facilitó la integración con el frontend.

La integración de la autenticación en el frontend fue un proceso de exploración y aprendizaje, especialmente porque la documentación para implementar autenticación local en Nuxt 3 aún es limitada. Sin embargo, una vez en su lugar, el control sobre las vistas accesibles para los usuarios autenticados se simplificó enormemente.

Finalmente, implementé un WebSocket en la vista de streaming para añadir un chat en vivo. Aunque era la primera vez que trabajaba con WebSockets, pude crear una implementación funcional utilizando varias bibliotecas y ejemplos. En el frontend, el desafío fue similar, donde configuré una librería para conectarse al WebSocket y realicé ajustes para permitir que múltiples clientes se conectaran y recibieran actualizaciones en tiempo real.



### Desarrollo Backend
El primer paso fue desarrollar la lógica para actualizar la playlist, lo que implicó varias iteraciones hasta encontrar una solución satisfactoria. Me enfrenté a desafíos como la gestión dinámica de los segmentos de video y la creación de endpoints robustos para el streaming.

### Desarrollo Frontend
Con el backend en su lugar, me dediqué al frontend, empleando Vue 3, Nuxt 3 y DaisyUI. Aquí, mi enfoque fue crear una interfaz de usuario moderna y reactiva, integrando con `hls.js` para una experiencia óptima de streaming.

## Resumen de Características

### Backend
- Actualización dinámica de playlist (m3u8).
- Endpoints para streaming de lista de reproducción y segmentos de video.
- Sistema de autenticación y gestión de usuarios con JWT.
- WebSocket para chat en tiempo real.

### Frontend
- Interfaz de usuario con Vue 3, Nuxt 3 y DaisyUI.
- Integración con `hls.js` para streaming.
- Autenticación y gestión de usuarios.
- Chat en vivo con conexión a WebSocket.


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
