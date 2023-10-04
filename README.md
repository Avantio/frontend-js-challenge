# Frontend JS Challenge
![atrends](./assets/readme/first.png)

Nuestros ingenieros de backend han implementado una sencilla API para acceder a la información y está accesible de manera pública en https://challenge.avantio.pro, sin embargo necesitarás enviar el token que te hemos enviado junto al enlace a este repositorio en una cabecera concreta de cada request, esta cabecera es `X-Avantio-Auth`. Esta cabecera ya se está enviando en cada petición que lo necesita gracias al interceptor ubicado en el fichero <code>[src/app/trends/auth-interceptor.ts](src/app/trends/auth-interceptor.ts)</code> y a la variables de entorno `avantioAPIAuthToken` definida en el fichero <code>[src/environments/environment.ts](src/environments/environment.ts)</code>. Lo único que tendrás que hacer respecto a esto es copiar el token que te hemos enviado en la variable de entorno `avantioAPIAuthToken` de dicho fichero.

Nuestros compañeras de UX/UI nos han dejado un diseño preparado en figma, para tener acceso a toda la funcionalidad de la plataforma es necesario el registro, es muy similar a Invision o Zeplin, así que si no lo has utilizado nunca no te preocupes, te harás con ella enseguida: https://www.figma.com/file/OZo8wGsr4aDns0lnOqYk39/Frontend-Challenge-atrendsPRO?node-id=0%3A1

En el diseño se aprecian dos vistas:
1. Listado de noticias
2. Detalle de noticia

Dentro del detalle de la noticia tenemos un slide-out que nos vale tanto para editar la noticia como para crearla.

Encontrarás todos los assets necesarios para la realización de la prueba dentro del directorio <code>[src/assets](src/assets)</code> del proyecto.

El sidebar es full height, aunque en el diseño no lo parezca, lo hemos hecho así para que se pudiese apreciar mejor la sección de las noticias.

En este repositorio se incluyen todos los ficheros necesarios para arrancar una aplicación de Angular en local que incluye: la vista del listado de noticias y la vista de detalle de cada noticia pulsando sobre ella.

Deberás modificar y/o ampliar el código existente para implementar las siguientes funcionalidades siguiendo el diseño indicado:

- Creación de noticias.
- Modificación de noticias.
- Eliminación de noticias.

## Tareas previas
- Clonar este repositorio y hacerlo público para que podamos acceder a él.
- Antes de empezar las tareas envíanos por e-mail el enlace del repositorio.
- Haz los commits que consideres oportunos conforme vayas desarrollando las diferentes tareas (Mínimo un commit por tarea).

## Que se espera de ti

> [!NOTE]
> Puedes usar cualquier versión de Angular.

Se valorará:
- La arquitectura del proyecto.
- La arquitectura de componentes.
- La claridad del código y de las hojas de estilo.
- La fidelidad del resultado (tanto desktop como responsive).

Se tendrá en cuenta también:
- Código preparado para producción.
- Entregar una solución que se pueda escalar o añadir funcionalidad con facilidad.
- Siéntete libre a la hora de añadir cualquier mejora de UX/UI.
- Utilización de patrones de arquitectura de datos.

> [!NOTE]
> Puedes hacer todas las mejoras visuales que consideres que aporten valor al diseño actual.

## Especificación del API

### Listado de noticias
Los endpoints de borrado de noticias y update, sobre noticias que no hayas creado con tu token, funcionarán a modo mockup, no  actualizarán ni borrarán noticias, pero la respuesta será la misma.
```
GET /v1/trends
X-Avantio-Auth: YOUR_TOKEN
HTTP 1.1 403 Forbidden
{
  authorized: false
}

HTTP/1.1 200
Response body
{
  "trends": [
    {
      "_id": "5e412653a0ccdd0f7ad122f7",
      "title": "El dueño de Panrico se da cuenta ahora de que los donuts salen con un agujero por un defecto de fábrica y entra en cólera",
      "body": "Después de visitar la factoría por primera vez desde que fundó la empresa en el año 1962, el dueño de Panrico ha entrado hoy en cólera tras darse cuenta de que los donuts tienen un agujero en medio debido a un defecto de fábrica.\n\n«¿Pero qué le habéis hecho a mi bollo?», ha exclamado el empresario frente a toda la plantilla, insistiendo en que «siempre me habéis dicho que todo estaba bien, y mira esto, mira este boquete enorme. ¡No me puedo fiar de vosotros!».\n\n"¡No me puedo creer que nadie me haya avisado de esto!", ha insistido entre gritos en medio de la fábrica. "¿Por qué salen así mis bollos y desde cuándo?", ha exclamado furioso. El dueño ha tirado al suelo miles de donuts y los ha pisado con rabia. "¿Pero cómo podemos estar vendiendo esta basura?", ha gritado fuera de sí. "¿Un agujero en medio? ¿Timando al personal? ¿Estamos locos? ¡Pero qué mierda habéis estado haciendo!", ha abroncado inconsolable.\n\nNo es la primera vez que el dueño de una importante compañía de alimentación recibe un disgusto semejante. En el año 2014, el fundador de Kinder despidió a más del 80% de su plantilla tras descubrir que llevaban décadas metiendo juguetes en el interior de sus huevos de chocolate.",
      "provider": "elmundo",
      "image": "https://emtstatic.com/2020/02/iStock-922747782.jpg",
      "url": "https://www.elmundotoday.com/2020/02/el-dueno-de-panrico-se-da-cuenta-ahora-de-que-los-donuts-salen-con-un-agujero-por-un-defecto-de-fabrica-y-entra-en-colera/",
      "createdAt": "2020-02-10T09:46:16.611Z"
    }
  ]
}
```

### Creación de noticias
Son necesarios todos los campos en el body de la petición
```
POST /v1/trends
X-Avantio-Auth: YOUR_TOKEN

Request body
{
	"title": "Un joven de Vigo dona doce horas extras a Amancio Ortega",
	"body": "\"SI TERMINARA EL TRABAJO EN SU JORNADA NORMAL COMO HACEMOS TODOS NO HARÍA FALTA QUE DONASE NADA\", CRITICA EL EMPRESARIO",
	"url": "https://www.elmundotoday.com/2020/02/un-joven-de-vigo-dona-doce-horas-extras-a-amancio-ortega/",
	"image": "https://emtstatic.com/2020/02/iStock-170222445.jpg",
	"provider": "elpais"
}

HTTP/1.1 403 Forbidden
{
  authorized: false
}

HTTP/1.1 200
Response body
{
  "trend": {
    "_id": "5e3d5468b6b80e00132096e0",
    "title": "Un joven de Vigo dona doce horas extras a Amancio Ortega",
    "body": "\"SI TERMINARA EL TRABAJO EN SU JORNADA NORMAL COMO HACEMOS TODOS NO HARÍA FALTA QUE DONASE NADA\", CRITICA EL EMPRESARIO",
    "url": "https://www.elmundotoday.com/2020/02/un-joven-de-vigo-dona-doce-horas-extras-a-amancio-ortega/",
    "image": "https://emtstatic.com/2020/02/iStock-170222445.jpg",
    "provider": "elpais"
    "token": "blfuaieusknuw4g1vdijb",
    "createdAt": "2020-02-07T12:13:28.323Z"
  }
}
```

### Actualización de noticias
No es necesario enviar todos los campos si lo que se quiere es una actualización parcial.
```
PUT /v1/trends/:trendId
X-Avantio-Auth: YOUR_TOKEN

Request body
{
	"title": "Un joven de Vigo dona once horas extras a Amancio Ortega",
}

HTTP/1.1 403 Forbidden
{
  authorized: false
}

HTTP/1.1 200
Response body
{
  "modified": 1
}
```

### Eliminación de noticias
```
DELETE /v1/trends/:trendId
X-Avantio-Auth: YOUR_TOKEN

HTTP/1.1 403 Forbidden
{
  authorized: false
}

HTTP 1.1 200
Response body
{
  success: true
}
```

### Detalle de noticia
```
GET /v1/trends/:trendId
X-Avantio-Auth: YOUR_TOKEN

HTTP/1.1 403 Forbidden
{
  authorized: false
}

HTTP/1.1 200
Response body
{
  "trend": {
    "_id": "5e3d5468b6b80e00132096e0",
    "title": "Un joven de Vigo dona doce horas extras a Amancio Ortega",
    "body": "\"SI TERMINARA EL TRABAJO EN SU JORNADA NORMAL COMO HACEMOS TODOS NO HARÍA FALTA QUE DONASE NADA\", CRITICA EL EMPRESARIO",
    "url": "https://www.elmundotoday.com/2020/02/un-joven-de-vigo-dona-doce-horas-extras-a-amancio-ortega/",
    "image": "https://emtstatic.com/2020/02/iStock-170222445.jpg",
    "provider": "elpais"
    "token": "blfuaieusknuw4g1vdijb",
    "createdAt": "2020-02-07T12:13:28.323Z"
  }
}
```