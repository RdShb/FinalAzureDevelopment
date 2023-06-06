## Tema 4: Implement containerized solutions	

- Preguntas: 

**¿Cuál es la diferencia entre Azure Container Registry, Azure Container Instances y Azure Container Apps?**

- Azure Container Registry (ACR) es un servicio de Azure que proporciona un registro privado para almacenar y administrar imágenes de contenedores. Permite a los desarrolladores y equipos de operaciones almacenar, administrar y desplegar imágenes de contenedores de forma segura y escalable.

- Azure Container Instances (ACI) es un servicio de Azure que permite ejecutar contenedores sin la necesidad de administrar una infraestructura subyacente. Permite a los usuarios ejecutar contenedores individuales de manera rápida y sencilla, sin preocuparse por el aprovisionamiento ni la administración de máquinas virtuales.

- Azure Container Apps es una plataforma de Azure que permite ejecutar y orquestar aplicaciones compuestas por múltiples contenedores. Proporciona un entorno de ejecución de aplicaciones más complejas, donde los contenedores pueden interactuar y comunicarse entre sí.

  

**¿Cómo se utiliza Azure Container Registry para almacenar y gestionar imágenes de contenedores?**

Para utilizar Azure Container Registry para almacenar y gestionar imágenes de contenedores, se deben seguir los siguientes pasos:

1. Crear un registro de contenedor en Azure Container Registry.
2. Configurar las opciones de acceso y seguridad del registro, como la autenticación y los roles de acceso.
3. Subir las imágenes de contenedor al registro utilizando herramientas como Docker CLI o Azure CLI.
4. Gestionar las imágenes en el registro, como etiquetar, actualizar o eliminar imágenes.
5. Configurar la integración del registro con otros servicios de Azure, como Azure Container Instances o Azure Kubernetes Service, para desplegar y ejecutar los contenedores.



**¿Cuál es el propósito y la ventaja de utilizar Azure Container Instances para ejecutar contenedores sin necesidad de administrar una infraestructura subyacente?**

El propósito de utilizar Azure Container Instances (ACI) es ejecutar contenedores de forma rápida y sencilla, sin tener que preocuparse por administrar la infraestructura subyacente. Algunas ventajas de utilizar ACI son:

- Rápido aprovisionamiento: Los contenedores se inician en cuestión de segundos, lo que permite una rápida escalabilidad y respuesta a la demanda.
- Facturación por segundos: Solo se paga por el tiempo en el que los contenedores están en ejecución, lo que proporciona un costo más preciso y granular.
- Flexibilidad: Permite ejecutar contenedores individuales sin la necesidad de utilizar orquestadores complejos como Kubernetes.
- Integración con servicios de Azure: ACI se integra fácilmente con otros servicios de Azure, como Azure Container Registry y Azure Functions, lo que permite construir soluciones más completas y escalables.



**Pregunta 6,página 29:**

Desarrollas una oferta de software como servicio (SaaS) para gestionar fotografías. Los usuarios cargan fotos a un servicio web que luego almacena las fotos en Azure Storage Blob Storage. El tipo de cuenta de almacenamiento es General Purpose V2.

Cuando se cargan las fotos, se deben procesar para producir y guardar una versión amigable para dispositivos móviles de la imagen. El proceso para producir una versión amigable para dispositivos móviles de la imagen debe iniciarse en menos de un minuto.

Necesitas diseñar el proceso que inicia el procesamiento de la foto.

Solución: Desencadenar el procesamiento de fotos a partir de eventos de Blob storage.

**¿Cumple la solución con el objetivo?**

A. Sí

B. No

**Respuesta correcta: B**

**Explicación:**

Necesitas capturar el evento desencadenado, por lo que debes mover el procesamiento de fotos a una Azure Function que se desencadene a partir de la carga del blob.

Nota: Los eventos de Azure Storage permiten que las aplicaciones reaccionen a eventos. Escenarios comunes de eventos de Blob storage incluyen el procesamiento de imágenes o videos, la indexación de búsqueda o cualquier flujo de trabajo orientado a archivos.

Los eventos se envían mediante Azure Event Grid a suscriptores como Azure Functions, Azure Logic Apps o incluso a su propio escuchador HTTP.

Nota: Solo las cuentas de almacenamiento de tipo StorageV2 (general purpose v2) y BlobStorage admiten la integración de eventos. El almacenamiento (general purpose v1) no admite la integración con Event Grid.

Referencia:

https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-event-overview





 **Pregunta 2, página 64:**

Necesitas almacenar los acuerdos de los usuarios.

¿Dónde deberías almacenar el acuerdo después de que se haya completado?

A. Cola de almacenamiento de Azure

B. Azure Event Hub

C. Tema de Azure Service Bus

D. Tema de Azure Event Grid

**Respuesta correcta: B**

**Explicación:**

Azure Event Hub se utiliza para telemetría y transmisión de datos distribuida.

Este servicio proporciona una solución única que permite la recuperación rápida de datos para el procesamiento en tiempo real, así como la reproducción repetida de datos sin procesar almacenados. Puede capturar los datos de transmisión en un archivo para su procesamiento y análisis. Tiene las siguientes características:

•  Baja latencia

•  Capacidad de recibir y procesar millones de eventos por segundo

•  Entrega al menos una vez

•  Referencia:

•  https://docs.microsoft.com/en-us/azure/event-grid/compare-messaging-services

 

**Caso de estudio 1,página 168:** 

**Descripción general**

Eres un desarrollador de Contoso, Ltd. La empresa tiene un sitio web de redes sociales que se desarrolla como una aplicación de página única (SPA, por sus siglas en inglés). La aplicación web principal para el sitio web de redes sociales carga contenido subido por usuarios desde el almacenamiento de blobs.

Estás desarrollando una solución para monitorear los datos cargados en busca de contenido inapropiado. El siguiente proceso ocurre cuando los usuarios cargan contenido utilizando la SPA:

• Se envían mensajes a ContentUploadService.

• El contenido es procesado por ContentAnalysisService.

• Después de que se completa el procesamiento, el contenido se publica en la red social o se publica un mensaje de rechazo en su lugar.

ContentAnalysisService se implementa con Azure Container Instances desde un Azure Container Registry privado llamado contosoimages.

La solución utilizará ocho núcleos de CPU.

Azure Active Directory

Contoso, Ltd. utiliza Azure Active Directory (Azure AD) tanto para cuentas internas como para cuentas de invitados.

**Requisitos**

-ContentAnalysisService:

El grupo de ciencia de datos de la empresa construyó ContentAnalysisService, que acepta contenido generado por el usuario como una cadena y devuelve un valor probable para contenido inapropiado. Cualquier valor por encima de un umbral específico debe ser revisado por un empleado de Contoso, Ltd.

Debes crear una función de Azure llamada CheckUserContent para realizar las comprobaciones de contenido.

-Costos:

Debes minimizar los costos de todos los servicios de Azure.

-Revisión manual:

Para revisar el contenido, el usuario debe autenticarse en la parte del sitio web de ContentAnalysisService utilizando sus credenciales de Azure AD. El sitio web está construido utilizando React y todas las páginas y puntos finales de API requieren autenticación. Para revisar el contenido, un usuario debe formar parte de un rol de ContentReviewer. Todas las revisiones completadas deben incluir la dirección de correo electrónico del revisor con fines de auditoría.

-Alta disponibilidad:

Todos los servicios deben ejecutarse en varias regiones. La falla de cualquier servicio en una región no debe afectar la disponibilidad general de la aplicación.

-Monitoreo:

Se debe generar una alerta si ContentUploadService utiliza más del 80 por ciento de los núcleos de CPU disponibles.

-Seguridad:

Tienes los siguientes requisitos de seguridad:

Cualquier servicio web accesible a través de Internet debe estar protegido contra ataques de scripting entre sitios.

Todos los sitios web y servicios deben utilizar SSL de una autoridad de certificación raíz válida.

Las claves de acceso a Azure Storage solo deben almacenarse en memoria y solo deben estar disponibles para el servicio.

Todos los servicios internos solo deben ser accesibles desde redes virtuales internas (VNets).

Todas las partes del sistema deben admitir restricciones de tráfico de entrada y salida.

Todas las llamadas de servicio deben autenticarse utilizando Azure AD.

-Acuerdos de usuario:

Cuando un usuario envía contenido, debe aceptar un acuerdo de usuario. El acuerdo permite a los empleados de Contoso, Ltd. revisar el contenido, almacenar cookies en los dispositivos de los usuarios y rastrear las direcciones IP de los usuarios.

La información sobre los acuerdos es utilizada por múltiples divisiones dentro de Contoso, Ltd.

Las respuestas de los usuarios no deben perderse y deben estar disponibles para todas las partes sin importar el tiempo de actividad del servicio individual.

Se espera que el volumen de acuerdos sea de millones por hora.

-Pruebas de validación:

Cuando haya disponible una nueva versión de ContentAnalysisService, se debe procesar la versión anterior de siete días de contenido con la nueva versión para verificar que la nueva versión no se desvíe significativamente de la versión anterior.

Problemas

Los usuarios de ContentUploadService informan que ocasionalmente ven respuestas HTTP 502 en páginas específicas.

**Código**

ContentUploadService

![image-20230605095857976](/Users/victorvitio/Library/Application Support/typora-user-images/image-20230605095857976.png)

![image-20230605095909145](/Users/victorvitio/Library/Application Support/typora-user-images/image-20230605095909145.png)





**Pregunta 14, página 103:**

Necesitas almacenar los acuerdos de los usuarios.

¿Dónde deberías almacenar el acuerdo después de que se haya completado?

A. Cola de almacenamiento de Azure

B. Azure Event Hub

C. Tema de Azure Service Bus

D. Tema de Azure Event Grid

Respuesta correcta: B

Sección: (ninguna)

Explicación:

Azure Event Hub se utiliza para telemetría y transmisión de datos distribuida.

Este servicio proporciona una solución única que permite la recuperación rápida de datos para el procesamiento en tiempo real, así como la reproducción repetida de datos sin procesar almacenados. Puede capturar los datos de transmisión en un archivo para su procesamiento y análisis. Tiene las siguientes características:

•  Baja latencia

•  Capacidad de recibir y procesar millones de eventos por segundo

•  Entrega al menos una vez

•  Referencia:

•  https://docs.microsoft.com/en-us/azure/event-grid/compare-messaging-services

 



