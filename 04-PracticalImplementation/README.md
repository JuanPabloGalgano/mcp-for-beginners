# Implementación Práctica

[![Cómo Construir, Probar y Desplegar Aplicaciones MCP con Herramientas y Flujos de Trabajo Reales](../images/video-thumbnails/05.png)](https://youtu.be/vCN9-mKBDfQ)

_(Haz clic en la imagen de arriba para ver el video de esta lección)_

La implementación práctica es donde el poder del Model Context Protocol (MCP) se vuelve tangible. Si bien comprender la teoría y la arquitectura detrás de MCP es importante, el valor real surge cuando aplicas estos conceptos para construir, probar y desplegar soluciones que resuelven problemas del mundo real. Este capítulo tiende un puente entre el conocimiento conceptual y el desarrollo práctico, guiándote a través del proceso de dar vida a las aplicaciones basadas en MCP.

Ya sea que estés desarrollando asistentes inteligentes, integrando IA en flujos de trabajo empresariales o construyendo herramientas personalizadas para el procesamiento de datos, MCP proporciona una base flexible. Su diseño agnóstico al lenguaje y los SDKs oficiales para los lenguajes de programación más populares lo hacen accesible a una amplia gama de desarrolladores. Al aprovechar estos SDKs, puedes prototipar, iterar y escalar rápidamente tus soluciones en diferentes plataformas y entornos.

En las siguientes secciones encontrarás ejemplos prácticos, código de muestra y estrategias de despliegue que demuestran cómo implementar MCP en C#, Java con Spring, TypeScript, JavaScript y Python. También aprenderás a depurar y probar tus servidores MCP, gestionar APIs y desplegar soluciones en la nube usando Azure. Estos recursos prácticos están diseñados para acelerar tu aprendizaje y ayudarte a construir con confianza aplicaciones MCP robustas y listas para producción.

## Descripción General

Esta lección se centra en los aspectos prácticos de la implementación de MCP en múltiples lenguajes de programación. Exploraremos cómo usar los SDKs de MCP en C#, Java con Spring, TypeScript, JavaScript y Python para construir aplicaciones robustas, depurar y probar servidores MCP, y crear recursos, prompts y herramientas reutilizables.

## Objetivos de Aprendizaje

Al finalizar esta lección, podrás:

- Implementar soluciones MCP usando SDKs oficiales en varios lenguajes de programación
- Depurar y probar servidores MCP de forma sistemática
- Crear y usar características de servidor (Recursos, Prompts y Herramientas)
- Diseñar flujos de trabajo MCP efectivos para tareas complejas
- Optimizar implementaciones MCP en cuanto a rendimiento y fiabilidad

## Recursos Oficiales de SDK

El Model Context Protocol ofrece SDKs oficiales para múltiples lenguajes (alineados con la [Especificación MCP 2025-11-25](https://spec.modelcontextprotocol.io/specification/2025-11-25/)):

- [SDK de C#](https://github.com/modelcontextprotocol/csharp-sdk)
- [SDK de Java con Spring](https://github.com/modelcontextprotocol/java-sdk) **Nota:** requiere dependencia de [Project Reactor](https://projectreactor.io). (Ver [problema de discusión 246](https://github.com/orgs/modelcontextprotocol/discussions/246).)
- [SDK de TypeScript](https://github.com/modelcontextprotocol/typescript-sdk)
- [SDK de Python](https://github.com/modelcontextprotocol/python-sdk)
- [SDK de Kotlin](https://github.com/modelcontextprotocol/kotlin-sdk)
- [SDK de Go](https://github.com/modelcontextprotocol/go-sdk)

## Trabajando con los SDKs de MCP

Esta sección proporciona ejemplos prácticos de implementación de MCP en múltiples lenguajes de programación. Puedes encontrar código de muestra en el directorio `samples` organizado por lenguaje.

### Muestras Disponibles

El repositorio incluye [implementaciones de muestra](./samples/) en los siguientes lenguajes:

- [C#](./samples/csharp/README.md)
- [Java con Spring](./samples/java/containerapp/README.md)
- [TypeScript](./samples/typescript/README.md)
- [JavaScript](./samples/javascript/README.md)
- [Python](./samples/python/README.md)

Cada muestra demuestra conceptos clave de MCP y patrones de implementación para ese lenguaje y ecosistema específico.

### Guías Prácticas

Guías adicionales para la implementación práctica de MCP:

- [Paginación y Conjuntos de Resultados Grandes](./pagination/README.md) - Maneja la paginación basada en cursores para herramientas, recursos y conjuntos de datos grandes

## Características Principales del Servidor

Los servidores MCP pueden implementar cualquier combinación de estas características:

### Recursos

Los recursos proporcionan contexto y datos para que el usuario o el modelo de IA los utilice:

- Repositorios de documentos
- Bases de conocimiento
- Fuentes de datos estructurados
- Sistemas de archivos

### Prompts

Los prompts son mensajes y flujos de trabajo con plantilla para los usuarios:

- Plantillas de conversación predefinidas
- Patrones de interacción guiada
- Estructuras de diálogo especializadas

### Herramientas

Las herramientas son funciones que el modelo de IA puede ejecutar:

- Utilidades de procesamiento de datos
- Integraciones con APIs externas
- Capacidades computacionales
- Funcionalidad de búsqueda

## Implementaciones de Muestra: Implementación en C#

El repositorio oficial del SDK de C# contiene varias implementaciones de muestra que demuestran diferentes aspectos de MCP:

- **Cliente MCP Básico**: Ejemplo simple que muestra cómo crear un cliente MCP y llamar herramientas
- **Servidor MCP Básico**: Implementación mínima de servidor con registro básico de herramientas
- **Servidor MCP Avanzado**: Servidor con todas las funciones, incluyendo registro de herramientas, autenticación y manejo de errores
- **Integración con ASP.NET**: Ejemplos que demuestran la integración con ASP.NET Core
- **Patrones de Implementación de Herramientas**: Varios patrones para implementar herramientas con diferentes niveles de complejidad

El SDK de MCP para C# está en versión preliminar y las APIs pueden cambiar. Actualizaremos continuamente este blog a medida que el SDK evolucione.

### Características Clave

- [C# MCP Nuget ModelContextProtocol](https://www.nuget.org/packages/ModelContextProtocol)
- Construyendo tu [primer Servidor MCP](https://devblogs.microsoft.com/dotnet/build-a-model-context-protocol-mcp-server-in-csharp/).

Para ejemplos completos de implementación en C#, visita el [repositorio oficial de muestras del SDK de C#](https://github.com/modelcontextprotocol/csharp-sdk)

## Implementación de Muestra: Implementación con Java y Spring

El SDK de Java con Spring ofrece opciones robustas de implementación de MCP con características de nivel empresarial.

### Características Clave

- Integración con Spring Framework
- Seguridad de tipos fuerte
- Soporte de programación reactiva
- Manejo de errores exhaustivo

Para una muestra completa de implementación con Java y Spring, consulta la [muestra de Java con Spring](samples/java/containerapp/README.md) en el directorio de muestras.

## Implementación de Muestra: Implementación en JavaScript

El SDK de JavaScript proporciona un enfoque ligero y flexible para la implementación de MCP.

### Características Clave

- Soporte para Node.js y navegadores
- API basada en promesas
- Fácil integración con Express y otros frameworks
- Soporte de WebSocket para streaming

Para una muestra completa de implementación en JavaScript, consulta la [muestra de JavaScript](samples/javascript/README.md) en el directorio de muestras.

## Implementación de Muestra: Implementación en Python

El SDK de Python ofrece un enfoque pythónico para la implementación de MCP con excelentes integraciones de frameworks de ML.

### Características Clave

- Soporte de async/await con asyncio
- Integración con FastAPI``
- Registro simple de herramientas
- Integración nativa con las bibliotecas de ML más populares

Para una muestra completa de implementación en Python, consulta la [muestra de Python](samples/python/README.md) en el directorio de muestras.

## Gestión de API

Azure API Management es una excelente respuesta a cómo podemos proteger los Servidores MCP. La idea es poner una instancia de Azure API Management delante de tu Servidor MCP y dejar que gestione las características que probablemente querrás, como:

- limitación de velocidad
- gestión de tokens
- monitoreo
- balanceo de carga
- seguridad

### Muestra de Azure

Aquí hay una muestra de Azure que hace exactamente eso, es decir, [crear un Servidor MCP y protegerlo con Azure API Management](https://github.com/Azure-Samples/remote-mcp-apim-functions-python).

Observa cómo ocurre el flujo de autorización en la imagen a continuación:

![APIM-MCP](https://github.com/Azure-Samples/remote-mcp-apim-functions-python/blob/main/mcp-client-authorization.gif?raw=true)

En la imagen anterior ocurre lo siguiente:

- La autenticación/autorización se realiza usando Microsoft Entra.
- Azure API Management actúa como puerta de enlace y usa políticas para dirigir y gestionar el tráfico.
- Azure Monitor registra todas las solicitudes para análisis posterior.

#### Flujo de autorización

Veamos el flujo de autorización con más detalle:

![Diagrama de Secuencia](https://github.com/Azure-Samples/remote-mcp-apim-functions-python/blob/main/infra/app/apim-oauth/diagrams/images/mcp-client-auth.png?raw=true)

#### Especificación de autorización MCP

Aprende más sobre la [especificación de Autorización MCP](https://spec.modelcontextprotocol.io/specification/2025-11-25/basic/authorization/)

## Desplegar Servidor MCP Remoto en Azure

Veamos si podemos desplegar la muestra que mencionamos anteriormente:

1. Clona el repositorio

    ```bash
    git clone https://github.com/Azure-Samples/remote-mcp-apim-functions-python.git
    cd remote-mcp-apim-functions-python
    ```

1. Registra el proveedor de recursos `Microsoft.App`.

   - Si estás usando Azure CLI, ejecuta `az provider register --namespace Microsoft.App --wait`.
   - Si estás usando Azure PowerShell, ejecuta `Register-AzResourceProvider -ProviderNamespace Microsoft.App`. Luego ejecuta `(Get-AzResourceProvider -ProviderNamespace Microsoft.App).RegistrationState` después de un tiempo para verificar si el registro está completo.

1. Ejecuta este comando de [azd](https://aka.ms/azd) para aprovisionar el servicio de gestión de API, la aplicación de funciones (con código) y todos los demás recursos de Azure necesarios

    ```shell
    azd up
    ```

    Este comando debería desplegar todos los recursos en la nube de Azure

### Probando tu servidor con MCP Inspector

1. En una **nueva ventana de terminal**, instala y ejecuta MCP Inspector

    ```shell
    npx @modelcontextprotocol/inspector
    ```

    Deberías ver una interfaz similar a:

    ![Conectar al inspector de Node](../03-GettingStarted/01-first-server/assets/connect.png)

1. Haz CTRL+clic para cargar la aplicación web MCP Inspector desde la URL que muestra la aplicación (por ejemplo, [http://127.0.0.1:6274/#resources](http://127.0.0.1:6274/#resources))
1. Establece el tipo de transporte en `SSE`
1. Establece la URL en el endpoint SSE de API Management en ejecución que se muestra después de `azd up` y haz clic en **Conectar**:

    ```shell
    https://<apim-servicename-from-azd-output>.azure-api.net/mcp/sse
    ```

1. **Lista de Herramientas**. Haz clic en una herramienta y **Ejecuta la Herramienta**.

Si todos los pasos han funcionado, ahora deberías estar conectado al servidor MCP y haber podido llamar a una herramienta.

## Servidores MCP para Azure

[Remote-mcp-functions](https://github.com/Azure-Samples/remote-mcp-functions-dotnet): Este conjunto de repositorios son plantillas de inicio rápido para construir y desplegar servidores MCP (Model Context Protocol) remotos personalizados usando Azure Functions con Python, C# .NET o Node/TypeScript.

Las muestras proporcionan una solución completa que permite a los desarrolladores:

- Construir y ejecutar localmente: Desarrollar y depurar un servidor MCP en una máquina local
- Desplegar en Azure: Desplegar fácilmente en la nube con un simple comando azd up
- Conectar desde clientes: Conectarse al servidor MCP desde varios clientes, incluyendo el modo agente de Copilot de VS Code y la herramienta MCP Inspector

### Características Clave

- Seguridad por diseño: El servidor MCP está protegido usando claves y HTTPS
- Opciones de autenticación: Admite OAuth usando autenticación incorporada y/o API Management
- Aislamiento de red: Permite el aislamiento de red usando Azure Virtual Networks (VNET)
- Arquitectura sin servidor: Aprovecha Azure Functions para una ejecución escalable y orientada a eventos
- Desarrollo local: Soporte integral de desarrollo local y depuración
- Despliegue simple: Proceso de despliegue simplificado hacia Azure

El repositorio incluye todos los archivos de configuración necesarios, el código fuente y las definiciones de infraestructura para comenzar rápidamente con una implementación de servidor MCP lista para producción.

- [Azure Remote MCP Functions Python](https://github.com/Azure-Samples/remote-mcp-functions-python) - Implementación de muestra de MCP usando Azure Functions con Python

- [Azure Remote MCP Functions .NET](https://github.com/Azure-Samples/remote-mcp-functions-dotnet) - Implementación de muestra de MCP usando Azure Functions con C# .NET

- [Azure Remote MCP Functions Node/Typescript](https://github.com/Azure-Samples/remote-mcp-functions-typescript) - Implementación de muestra de MCP usando Azure Functions con Node/TypeScript.

## Conclusiones Clave

- Los SDKs de MCP proporcionan herramientas específicas de cada lenguaje para implementar soluciones MCP robustas
- El proceso de depuración y pruebas es fundamental para aplicaciones MCP fiables
- Las plantillas de prompts reutilizables permiten interacciones consistentes con la IA
- Los flujos de trabajo bien diseñados pueden orquestar tareas complejas usando múltiples herramientas
- Implementar soluciones MCP requiere considerar la seguridad, el rendimiento y el manejo de errores

## Ejercicio

Diseña un flujo de trabajo MCP práctico que aborde un problema del mundo real en tu dominio:

1. Identifica 3-4 herramientas que serían útiles para resolver este problema
2. Crea un diagrama de flujo que muestre cómo interactúan estas herramientas
3. Implementa una versión básica de una de las herramientas usando tu lenguaje preferido
4. Crea una plantilla de prompt que ayude al modelo a usar tu herramienta de manera efectiva

## Recursos Adicionales

---

## Qué Sigue

Siguiente: [Temas Avanzados](../05-AdvancedTopics/README.md)
