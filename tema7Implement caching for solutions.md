## Tema 4: Implement caching for solutions

- Preguntas: 

**¿Qué es la caché y cómo puede mejorar el rendimiento de una aplicación?**

La caché es una técnica utilizada en el desarrollo de software para almacenar temporalmente datos o resultados de operaciones costosas en un lugar de acceso rápido, como la memoria, con el fin de mejorar el rendimiento de una aplicación. En lugar de realizar operaciones repetitivas o costosas cada vez que se necesita un dato o resultado, se busca en la caché y, si el dato está presente, se devuelve rápidamente sin tener que realizar la operación nuevamente.

**¿Cuáles son las opciones de caché disponibles en Azure?	**

En Azure, hay varias opciones de caché disponibles que se pueden utilizar para mejorar el rendimiento de una aplicación:

1. Azure Redis Cache: Es un servicio de caché completamente administrado basado en Redis. Proporciona una caché de datos de alta velocidad y baja latencia que puede ayudar a reducir la carga en las bases de datos y mejorar el rendimiento de las aplicaciones.
2. Azure Managed Cache Service: Este servicio ha sido reemplazado por Azure Redis Cache. Proporcionaba una caché en memoria para aplicaciones web y móviles.
3. Azure Cache for Redis: Es una opción de caché basada en Redis que permite almacenar datos en memoria de forma persistente y altamente disponible. Proporciona características avanzadas de caché, como particionamiento, alta disponibilidad y replicación.
4. Azure CDN (Content Delivery Network): Aunque no es una caché en sí misma, Azure CDN se puede utilizar para almacenar en caché contenido estático, como imágenes, archivos CSS y JavaScript, en servidores distribuidos globalmente. Esto mejora el rendimiento al servir el contenido desde el servidor más cercano al usuario, reduciendo la latencia.



**¿Cómo se implementa y se utiliza la caché en una solución en Azure?**

Para implementar y utilizar la caché en una solución en Azure, se pueden seguir los siguientes pasos generales:

1. Crear una instancia de caché utilizando el servicio correspondiente en Azure, como Azure Redis Cache.
2. Configurar la caché con las opciones adecuadas, como la capacidad, la replicación y la seguridad.
3. En la aplicación, determinar qué datos o resultados deben almacenarse en caché y por cuánto tiempo. Esto puede variar según las necesidades y la lógica de la aplicación.
4. Antes de realizar una operación costosa o repetitiva, consultar la caché para ver si los datos requeridos están presentes. Si es así, utilizar los datos de la caché en lugar de realizar la operación.
5. Si los datos no están en la caché, realizar la operación necesaria para obtenerlos y luego almacenarlos en la caché para futuros usos.





**Pregunta 11,página 191:**

Estás desarrollando e implementando varias aplicaciones web ASP.NET en Azure App Service. Planeas guardar la información del estado de sesión y la salida HTML.

Debes utilizar un mecanismo de almacenamiento con los siguientes requisitos:

Compartir el estado de sesión en todas las aplicaciones web ASP.NET.

Admitir acceso controlado y concurrente a los mismos datos de estado de sesión para múltiples lectores y un solo escritor.

Guardar respuestas HTTP completas para solicitudes concurrentes.

Necesitas almacenar la información.

Solución propuesta: Implementa y configura una base de datos de Azure para PostgreSQL. Actualiza las aplicaciones web.

**¿Cumple la solución con el objetivo?**

A. Sí

B. No

**Respuesta correcta: B**

**Explicación:**

En lugar de eso, implementa y configura Azure Cache for Redis. Actualiza las aplicaciones web.

Referencia:

https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching#managing-concurrency-in-a-cache



**Pregunta 10,página 202:**

Estás desarrollando e implementando varias aplicaciones web ASP.NET en Azure App Service. Planeas guardar la información del estado de sesión y la salida HTML.

Debes utilizar un mecanismo de almacenamiento con los siguientes requisitos:

Compartir el estado de sesión entre todas las aplicaciones web ASP.NET.

Admitir acceso controlado y concurrente a los mismos datos de estado de sesión para múltiples lectores y un único escritor.

Guardar respuestas HTTP completas para solicitudes concurrentes.

Necesitas almacenar la información.

**Solución propuesta: **Habilitar Application Request Routing (ARR).

**¿Cumple la solución con el objetivo?**

A. Sí

B. No

**Respuesta correcta: B**

Explicación:

En su lugar, implementa y configura Azure Cache for Redis. Actualiza las aplicaciones web.

Referencia:

https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching#managing-concurrency-in-acache



**Pregunta 11,página 203:** 

Estás desarrollando e implementando varias aplicaciones web ASP.NET en Azure App Service. Planeas guardar la información del estado de sesión y la salida HTML.

Debes utilizar un mecanismo de almacenamiento con los siguientes requisitos:

Compartir el estado de sesión en todas las aplicaciones web ASP.NET.

Admitir acceso controlado y concurrente a los mismos datos de estado de sesión para múltiples lectores y un solo escritor.

Guardar respuestas HTTP completas para solicitudes concurrentes.

Necesitas almacenar la información.

Solución propuesta: Implementa y configura Azure Cache for Redis. Actualiza las aplicaciones web.

**¿Cumple la solución con el objetivo?**

A. Sí

B. No

**Respuesta correcta: A**

**Explicación:**

El proveedor de estado de sesión para Azure Cache for Redis te permite compartir información de sesión entre diferentes instancias de una aplicación web ASP.NET.

La misma conexión puede ser utilizada por múltiples hilos concurrentes.

Redis admite operaciones de lectura y escritura.

El proveedor de caché de salida para Azure Cache for Redis te permite guardar las respuestas HTTP generadas por una aplicación web ASP.NET.

Nota: Usando el portal de Azure, también puedes configurar la política de eliminación de la caché y controlar el acceso a la caché agregando usuarios a los roles proporcionados. Estos roles, que definen las operaciones que los miembros pueden realizar, incluyen Owner, Contributor y Reader. Por ejemplo, los miembros del rol Owner tienen control completo sobre la caché (incluyendo la seguridad) y su contenido, los miembros del rol Contributor pueden leer y escribir información en la caché, y los miembros del rol Reader solo pueden recuperar datos de la caché.

Referencia:

https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching













