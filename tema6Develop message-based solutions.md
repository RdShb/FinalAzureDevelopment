## Tema 6: Develop message-based solutions

- Preguntas: 

**¿Cuál es la diferencia entre Azure Message Queue, Azure Service Bus y Azure Queue Storage en términos de funcionalidad y casos de uso?	**

- Azure Message Queue, Azure Service Bus y Azure Queue Storage son servicios de mensajería ofrecidos por Microsoft Azure, pero tienen diferencias en términos de funcionalidad y casos de uso.

Azure Message Queue (Azure Queue Storage): Es un servicio de cola simple y de baja latencia que permite enviar y recibir mensajes entre componentes de una aplicación. Es adecuado para escenarios donde se necesita una comunicación asíncrona y fiable entre componentes. Se utiliza principalmente para el procesamiento de trabajos en segundo plano, la coordinación de tareas y la implementación de patrones de mensajería pub/sub. Los mensajes se almacenan en cola y se procesan en el orden en que se reciben.

Azure Service Bus: Es un servicio de mensajería avanzado y altamente escalable que admite tanto colas como temas. Proporciona funcionalidades adicionales como el enrutamiento de mensajes basado en reglas, la suscripción a temas y la mensajería temporal. Azure Service Bus es adecuado para escenarios de mensajería más complejos, como la comunicación entre aplicaciones distribuidas, la transmisión de eventos en tiempo real y la implementación de patrones de mensajería pub/sub. También ofrece capacidades avanzadas de programación, como las transacciones y el procesamiento de mensajes en lotes.

Azure Queue Storage: Es un servicio de almacenamiento de colas que permite el almacenamiento y recuperación de mensajes en cola de manera segura y duradera. Aunque comparte el nombre "cola" con Azure Message Queue, es importante destacar que Azure Queue Storage es un servicio de almacenamiento en lugar de un servicio de mensajería completo. Se utiliza para escenarios donde se necesita una cola de mensajes simple sin la necesidad de características avanzadas de mensajería o en situaciones donde se requiere un almacenamiento persistente de mensajes.



**¿Cómo se utiliza Azure Message Queue para el envío y recepción de mensajes entre componentes de una aplicación distribuida?**

Para utilizar Azure Message Queue en el envío y recepción de mensajes entre componentes de una aplicación distribuida, se siguen los siguientes pasos:

1. Crear una instancia de Azure Message Queue y obtener las credenciales de conexión.
2. En el componente emisor, se utiliza el cliente de Azure Message Queue para enviar mensajes a la cola especificada. Esto implica crear un mensaje y enviarlo a la cola mediante la conexión y las credenciales proporcionadas.
3. En el componente receptor, se utiliza el cliente de Azure Message Queue para recibir mensajes de la cola especificada. Esto implica establecer una conexión con la cola y recibir mensajes en orden secuencial.
4. El componente receptor procesa los mensajes recibidos según la lógica de la aplicación.

**¿Cuál es el propósito y la ventaja de utilizar Azure Service Bus en comparación con otros servicios de mensajería?**

El propósito y la ventaja de utilizar Azure Service Bus en comparación con otros servicios de mensajería radica en sus características avanzadas y su escalabilidad. Algunas ventajas son:

1. Mensajería avanzada: Azure Service Bus ofrece funcionalidades como el enrutamiento de mensajes basado en reglas, la mensajería temporal, las transacciones y el procesamiento de mensajes en lotes. Esto permite implementar patrones de mensajería más complejos y adaptar la lógica de mensajería a las necesidades específicas de la aplicación.
2. Escalabilidad: Azure Service Bus está diseñado para manejar cargas de trabajo de mensajería a gran escala. Puede manejar millones de mensajes por segundo y proporciona una alta disponibilidad y confiabilidad en entornos distribuidos.
3. Compatibilidad con protocolos y lenguajes: Azure Service Bus admite varios protocolos y se puede acceder a través de diferentes lenguajes de programación. Esto permite la integración con una amplia gama de aplicaciones y sistemas existentes.
4. Publicación/Suscripción: Azure Service Bus admite el patrón de mensajería pub/sub, lo que significa que los mensajes se pueden publicar en un tema y los suscriptores interesados pueden recibirlos. Esto permite una comunicación flexible y desacoplada entre componentes distribuidos.

**Pregunta 16,página 105 :**

Una aplicación .NET necesita recibir un mensaje cada vez que una máquina virtual de Azure finaliza el procesamiento de datos. Los mensajes NO deben persistir después de ser procesados por la aplicación receptora.

Debes implementar el objeto .NET que recibirá los mensajes.

**¿Qué objeto debes usar?**

A. QueueClient

B. SubscriptionClient

C. TopicClient

D. CloudQueueClient

**Respuesta correcta: D**

**Explicación:**

Una cola permite el procesamiento de un mensaje por un solo consumidor. Se necesita un CloudQueueClient para acceder a la máquina virtual de Azure.

**Respuestas incorrectas:**

B, C: A diferencia de las colas, los temas y las suscripciones proporcionan una forma de comunicación uno a muchos en un patrón de publicación y suscripción. Es útil para escalar a un gran número de destinatarios.

Referencia:

https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-queues-topics-subscriptions



 **Pregunta 2, página 219**

Necesitas asegurarte de que todos los mensajes de Azure Event Grid sean procesados.

**¿Qué deberías utilizar?**

A. Azure Event Grid topic

B. Azure Service Bus topic

C. Azure Service Bus queue

D. Azure Storage queue

E. Azure Logic App custom connector

**Respuesta correcta: C**

**Explicación:**

Como arquitecto/desarrollador de soluciones, deberías considerar el uso de colas de Service Bus cuando:

Tu solución necesita recibir mensajes sin tener que sondear la cola. Con Service Bus, puedes lograrlo utilizando una operación de recepción de larga duración mediante los protocolos basados en TCP que admite Service Bus.

Referencia:

https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-azure-and-service-bus-queuescompared-contrasted

 

**Pregunta 4,página 230:** 

Estás desarrollando una aplicación de servicio de Azure que procesa datos de una cola cuando recibe un mensaje de una aplicación móvil. Los mensajes pueden no ser enviados al servicio de manera consistente. Tienes los siguientes requisitos:

- El tamaño de la cola no debe crecer más de 80 gigabytes (GB).

- Utilizar el orden primero en entrar, primero en salir (FIFO) de los mensajes.

- Minimizar los costos de Azure. Necesitas implementar la solución de mensajería. 

  **Solución: **

  Utiliza la API de .NET para agregar un mensaje a una cola de almacenamiento de Azure desde la aplicación móvil. Crea una máquina virtual de Azure que se active a partir de eventos de la cola de almacenamiento de Azure. 

  **¿Cumple la solución con el objetivo? **

  A. Sí

  B. No 

  **Respuesta correcta: B **

  **Explicación: **

  No uses una máquina virtual, en su lugar, crea una aplicación de función de Azure que utilice un desencadenador de cola de Azure Service Bus. 

  Referencia: https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-storage-queue-triggered-function
