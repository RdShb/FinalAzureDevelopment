# Tema 3: Develop event-based solutions

### ¿Qué son las soluciones basadas en eventos y cómo se diferencian de las arquitecturas tradicionales basadas en solicitudes y respuestas?
Las soluciones basadas en eventos son un enfoque arquitectónico en el cual las acciones y respuestas se desencadenan por eventos que ocurren en el sistema.
Estos eventos pueden ser generados por usuarios, dispositivos, aplicaciones o servicios, y se propagan a través de un bus de eventos o un sistema similar.

A diferencia de las arquitecturas tradicionales basadas en solicitudes y respuestas, donde los componentes se comunican directamente entre sí a través de llamadas sincrónicas,
las soluciones basadas en eventos se basan en la emisión y recepción de eventos asincrónicos. Cuando un evento ocurre, se notifica a los componentes interesados y estos pueden actuar en consecuencia.
Esta separación de la lógica de negocio de la generación de eventos permite una mayor flexibilidad, escalabilidad y desacoplamiento entre los diferentes componentes de la solución.


### ¿Cuál es el papel de Azure Event Grid en la implementación de soluciones basadas en eventos y cómo se integra con otros servicios de Azure?
Azure Event Grid es un servicio de enrutamiento de eventos administrado que desempeña un papel fundamental en la implementación de soluciones basadas en eventos dentro de Azure ya que proporciona un mecanismo para la entrega confiable y escalable de eventos.
El papel de Azure Event Grid es actuar como el bus de eventos centralizado en la arquitectura, permitiendo que los diferentes servicios publiquen eventos y que otros servicios los consuman.


### ¿Cuáles son los beneficios y casos de uso comunes de Azure Event Hub en el procesamiento y análisis de flujos masivos de eventos en tiempo real?	

Azure Event Hubs es un servicio de Azure diseñado específicamente para el procesamiento y análisis de flujos masivos de eventos en tiempo real.
Proporciona una plataforma escalable y confiable para la ingesta, retención y entrega de eventos a escala, lo que ofrece una serie de beneficios y casos de uso comunes, algunos de ellos son:

- Escalabilidad y rendimiento: Event Hubs puede manejar grandes volúmenes de eventos por segundo, lo que lo hace ideal para escenarios de alto rendimiento. 

- Retención de datos: Event Hubs permite la retención de eventos durante un período de tiempo configurable, lo que significa que los eventos se pueden almacenar para su posterior procesamiento y análisis.

- Procesamiento en tiempo real: Event Hubs facilita el procesamiento de eventos en tiempo real. Puedes conectar servicios de Azure como Azure Functions, Azure Stream Analytics o Azure Databricks para procesar y analizar eventos a medida que llegan.

- Análisis de datos en tiempo real: Event Hubs se integra con Azure Stream Analytics y Azure Databricks, lo que permite realizar análisis en tiempo real sobre los flujos de eventos. 

- Integración con otros servicios de Azure: Event Hubs se integra con una amplia gama de servicios de Azure, como Azure Functions, Azure Logic Apps, Azure Event Grid y Azure Storage.

### QUESTION 2 Pag 64
You need to store the user agreements.
Where should you store the agreement after it is completed?
A. Azure Storage queue
B. Azure Event Hub
C. Azure Service Bus topic
D. Azure Event Grid topic
Correct Answer: B

Explanation:
Azure Event Hub is used for telemetry and distributed data streaming.
This service provides a single solution that enables rapid data retrieval for real-time processing as well as
repeated replay of stored raw data. It can capture the streaming data into a file for processing and analysis.
It has the following characteristics:
low latency
capable of receiving and processing millions of events per second
at least once delivery


### QUESTION 6 Pag 147
You develop an app that allows users to upload photos and videos to Azure storage. The app uses a
storage REST API call to upload the media to a blob storage account named Account1. You have blob
storage containers named Container1 and Container2.
Uploading of videos occurs on an irregular basis.
You need to copy specific blobs from Container1 to Container2 when a new video is uploaded.
What should you do?

A. Copy blobs to Container2 by using the Put Blob operation of the Blob Service REST API
B. Create an Event Grid topic that uses the Start-AzureStorageBlobCopy cmdlet
C. Use AzCopy with the Snapshot switch to copy blobs to Container2
D. Download the blob to a virtual machine and then upload the blob to Container2
Correct Answer: B

Explanation:
The Start-AzureStorageBlobCopy cmdlet starts to copy a blob.
Example 1: Copy a named blob
C:\PS>Start-AzureStorageBlobCopy -SrcBlob "ContosoPlanning2015" -DestContainer "ContosoArchives" -
SrcContainer "ContosoUploads"
This command starts the copy operation of the blob named ContosoPlanning2015 from the container
named ContosoUploads to the container named ContosoArchives.

### QUESTION 15 Pag 104
You are developing an Azure solution to collect point-of-sale (POS) device data from 2,000 stores located
throughout the world. A single device can produce 2 megabytes (MB) of data every 24 hours. Each store
location has one to five devices that send data.
You must store the device data in Azure Blob storage. Device data must be correlated based on a device
identifier. Additional stores are expected to open in the future.
You need to implement a solution to receive the device data.
Solution: Provision an Azure Event Grid. Configure the machine identifier as the partition key and enable
capture.
Does the solution meet the goal?
A. Yes
B. No
Correct Answer: A
