# Tema 5:	Implement API Management

### ¿Qué es Azure API Management y cuál es su propósito en el desarrollo de aplicaciones?	
Azure API Management es un servicio de administración de API en la plataforma de computación en la nube de Microsoft, conocida como Azure.
Su propósito principal es facilitar la gestión y el control de las API utilizadas en el desarrollo de aplicaciones.

El propósito de Azure API Management es permitir a las organizaciones exponer, proteger y administrar sus API de manera segura y escalable. 
Proporciona un conjunto de herramientas y características que ayudan a simplificar la implementación, supervisión, seguridad, versionado y monetización de las API.

### ¿Cuáles son los beneficios de utilizar Azure API Management para gestionar APIs en una arquitectura de microservicios?	

Azure API Management es una herramienta que ofrece diversos beneficios para gestionar APIs en una arquitectura de microservicios. Permite administrar todas las APIs desde una interfaz centralizada, aplicar políticas de seguridad, escalar y optimizar el rendimiento, controlar cambios y versiones, monitorear el uso de las APIs, ofrecer un portal personalizado para desarrolladores y habilitar modelos de negocio para la monetización de los servicios. 

### ¿Cómo se configura y se utiliza Azure API Management para controlar el acceso y la seguridad de las APIs?	

Comienza creando un servicio de Azure API Management en el portal de Azure. Proporciona los detalles básicos, como el nombre, la suscripción y el grupo de recursos.

Después, registra la API que deseas administrar en Azure API Management. Puedes registrar una API existente o crear una nueva, especificando información relevante como la URL, la descripción y los parámetros.

Una vez registrada la API, es el momento de configurar políticas de seguridad para controlar el acceso a tus APIs. Azure API Management ofrece una amplia variedad de opciones para ello. Puedes establecer políticas de autenticación y autorización para garantizar que solo los usuarios autorizados puedan acceder a tus APIs.

En cuanto a la autenticación, tienes la posibilidad de configurar diferentes métodos según tus necesidades. Puedes utilizar claves de suscripción, tokens de acceso, certificados u otros mecanismos de autenticación para validar las solicitudes de los usuarios.

### QUESTION 8 Pag 148
Your company is developing an Azure API.
You need to implement authentication for the Azure API. You have the following requirements:
All API calls must be secure.
Callers to the API must not send credentials to the API.
Which authentication mechanism should you use?

A. Basic

B. Anonymous

C. Managed identity

D. Client certificate


Correct Answer: C

Explanation:
Use the authentication-managed-identity policy to authenticate with a backend service using the managed
identity of the API Management service. This policy essentially uses the managed identity to obtain an
access token from Azure Active Directory for accessing the specified resource. After successfully obtaining
the token, the policy will set the value of the token in the Authorization header using the Bearer scheme.

### QUESTION 9 Pag 149

You are a developer for a SaaS company that offers many web services.
All web services for the company must meet the following requirements:
Use API Management to access the services
Use OpenID Connect for authentication
Prevent anonymous usage
A recent security audit found that several web services can be called without any authentication.
Which API Management policy should you implement?

A. jsonp

B. authentication-certificate

C. check-header

D. validate-jwt


Correct Answer: D
Explanation:
Add the validate-jwt policy to validate the OAuth token for every incoming request.

Incorrect Answers:
A: The jsonp policy adds JSON with padding (JSONP) support to an operation or an API to allow crossdomain
calls from JavaScript browser-based clients. JSONP is a method used in JavaScript programs to
request data from a server in a different domain. JSONP bypasses the limitation enforced by most web
browsers where access to web pages must be in the same domain.
JSONP - Adds JSON with padding (JSONP) support to an operation or an API to allow cross-domain calls
from JavaScript browser-based clients.

### QUESTION 26 Pag 166

Your company is developing an Azure API hosted in Azure.
You need to implement authentication for the Azure API to access other Azure resources. You have the
following requirements:
All API calls must be authenticated.
Callers to the API must not send credentials to the API.
Which authentication mechanism should you use?

A. Basic

B. Anonymous

C. Managed identity

D. Client certificate


Correct Answer: C

Explanation:
Azure Active Directory Managed Service Identity (MSI) gives your code an automatically managed identity
for authenticating to Azure services, so that you can keep credentials out of your code.

Incorrect Answers:
A: Use the authentication-basic policy to authenticate with a backend service using Basic authentication.
This policy effectively sets the HTTP Authorization header to the value corresponding to the credentials
provided in the policy.
B: Anonymous is no authentication at all.
D: Your code needs credentials to authenticate to cloud services, but you want to limit the visibility of those
credentials as much as possible. Ideally, they never appear on a developer’s workstation or get checked-in
to source control. Azure Key Vault can store credentials securely so they aren’t in your code, but to retrieve
them you need to authenticate to Azure Key Vault. To authenticate to Key Vault, you need a credential! A
classic bootstrap problem.

