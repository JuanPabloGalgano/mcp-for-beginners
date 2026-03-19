## Primeros Pasos

[![Build Your First MCP Server](../images/video-thumbnails/04.png)](https://youtu.be/sNDZO9N4m9Y)

_(Haz clic en la imagen de arriba para ver el video de esta lección)_

Esta sección consta de varias lecciones:

- **1 Tu primer servidor**, en esta primera lección, aprenderás cómo crear tu primer servidor e inspeccionarlo con la herramienta inspector, una forma muy útil de probar y depurar tu servidor, [ir a la lección](01-first-server/README.md)

- **2 Cliente**, en esta lección, aprenderás cómo escribir un cliente que pueda conectarse a tu servidor, [ir a la lección](02-client/README.md)

- **3 Cliente con LLM**, una forma aún mejor de escribir un cliente es agregándole un LLM para que pueda "negociar" con tu servidor qué hacer, [ir a la lección](03-llm-client/README.md)

- **4 Consumir un servidor en modo GitHub Copilot Agent en Visual Studio Code**. Aquí veremos cómo ejecutar nuestro servidor MCP desde dentro de Visual Studio Code, [ir a la lección](04-vscode/README.md)

- **5 Servidor de transporte stdio** El transporte stdio es el estándar recomendado para la comunicación local entre servidor y cliente MCP, proporcionando comunicación segura basada en subprocesos con aislamiento de procesos integrado [ir a la lección](05-stdio-server/README.md)

- **6 HTTP Streaming con MCP (Streamable HTTP)**. Aprende sobre el transporte moderno de streaming HTTP (el enfoque recomendado para servidores MCP remotos según la [MCP Specification 2025-11-25](https://spec.modelcontextprotocol.io/specification/2025-11-25/basic/transports/#streamable-http)), notificaciones de progreso, y cómo implementar servidores y clientes MCP escalables en tiempo real usando Streamable HTTP. [ir a la lección](06-http-streaming/README.md)

- **7 Uso de AI Toolkit para VSCode** para consumir y probar tus clientes y servidores MCP [ir a la lección](07-aitk/README.md)

- **8 Pruebas**. Aquí nos enfocaremos especialmente en cómo podemos probar nuestro servidor y cliente de diferentes maneras, [ir a la lección](08-testing/README.md)

- **9 Despliegue**. Este capítulo verá diferentes formas de desplegar tus soluciones MCP, [ir a la lección](09-deployment/README.md)

- **10 Uso avanzado del servidor**. Este capítulo cubre el uso avanzado del servidor, [ir a la lección](./10-advanced/README.md)

- **11 Autenticación**. Este capítulo cubre cómo agregar autenticación simple, desde Basic Auth hasta el uso de JWT y RBAC. Se te recomienda comenzar aquí y luego revisar los Temas Avanzados en el Capítulo 5 y realizar un endurecimiento de seguridad adicional mediante las recomendaciones del Capítulo 2, [ir a la lección](./11-simple-auth/README.md)

- **12 Hosts MCP**. Configura y usa clientes host MCP populares incluyendo Claude Desktop, Cursor, Cline y Windsurf. Aprende sobre tipos de transporte y resolución de problemas, [ir a la lección](./12-mcp-hosts/README.md)

- **13 Inspector MCP**. Depura y prueba tus servidores MCP de forma interactiva usando la herramienta MCP Inspector. Aprende a solucionar problemas con herramientas, recursos y mensajes de protocolo, [ir a la lección](./13-mcp-inspector/README.md)

- **14 Muestreo**. Crea servidores MCP que colaboren con clientes MCP en tareas relacionadas con LLM. [ir a la lección](./14-sampling/README.md)

- **15 Aplicaciones MCP**. Construye servidores MCP que también respondan con instrucciones de UI, [ir a la lección](./15-mcp-apps/README.md)

El Protocolo de Contexto de Modelos (MCP) es un protocolo abierto que estandariza cómo las aplicaciones proporcionan contexto a los LLMs. Piensa en MCP como un puerto USB-C para aplicaciones de IA: proporciona una forma estandarizada de conectar modelos de IA a diferentes fuentes de datos y herramientas.

## Objetivos de Aprendizaje

Al final de esta lección, serás capaz de:

- Configurar entornos de desarrollo para MCP en C#, Java, Python, TypeScript y JavaScript
- Construir y desplegar servidores MCP básicos con características personalizadas (recursos, prompts y herramientas)
- Crear aplicaciones host que se conecten a servidores MCP
- Probar y depurar implementaciones MCP
- Comprender los desafíos comunes de configuración y sus soluciones
- Conectar tus implementaciones MCP a servicios LLM populares

## Configuración de tu Entorno MCP

Antes de comenzar a trabajar con MCP, es importante preparar tu entorno de desarrollo y comprender el flujo de trabajo básico. Esta sección te guiará a través de los pasos iniciales de configuración para garantizar un comienzo fluido con MCP.

### Requisitos Previos

Antes de adentrarte en el desarrollo de MCP, asegúrate de tener:

- **Entorno de Desarrollo**: Para el lenguaje que hayas elegido (C#, Java, Python, TypeScript o JavaScript)
- **IDE/Editor**: Visual Studio, Visual Studio Code, IntelliJ, Eclipse, PyCharm o cualquier editor de código moderno
- **Gestores de Paquetes**: NuGet, Maven/Gradle, pip o npm/yarn
- **Claves de API**: Para cualquier servicio de IA que planees usar en tus aplicaciones host


### SDKs Oficiales

En los próximos capítulos verás soluciones construidas usando Python, TypeScript, Java y .NET. Aquí están todos los SDKs oficialmente soportados.

MCP proporciona SDKs oficiales para múltiples lenguajes (alineados con la [MCP Specification 2025-11-25](https://spec.modelcontextprotocol.io/specification/2025-11-25/)):
- [C# SDK](https://github.com/modelcontextprotocol/csharp-sdk) - Mantenido en colaboración con Microsoft
- [Java SDK](https://github.com/modelcontextprotocol/java-sdk) - Mantenido en colaboración con Spring AI
- [TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk) - La implementación oficial de TypeScript
- [Python SDK](https://github.com/modelcontextprotocol/python-sdk) - La implementación oficial de Python (FastMCP)
- [Kotlin SDK](https://github.com/modelcontextprotocol/kotlin-sdk) - La implementación oficial de Kotlin
- [Swift SDK](https://github.com/modelcontextprotocol/swift-sdk) - Mantenido en colaboración con Loopwork AI
- [Rust SDK](https://github.com/modelcontextprotocol/rust-sdk) - La implementación oficial de Rust
- [Go SDK](https://github.com/modelcontextprotocol/go-sdk) - La implementación oficial de Go

## Conclusiones Clave

- Configurar un entorno de desarrollo MCP es sencillo con los SDKs específicos para cada lenguaje
- Construir servidores MCP implica crear y registrar herramientas con esquemas claros
- Los clientes MCP se conectan a servidores y modelos para aprovechar capacidades extendidas
- Las pruebas y la depuración son esenciales para implementaciones MCP confiables
- Las opciones de despliegue van desde el desarrollo local hasta soluciones basadas en la nube

## Práctica

Tenemos un conjunto de muestras que complementan los ejercicios que verás en todos los capítulos de esta sección. Además, cada capítulo también tiene sus propios ejercicios y tareas

- [Java Calculator](./samples/java/calculator/README.md)
- [.Net Calculator](./samples/csharp/)
- [JavaScript Calculator](./samples/javascript/README.md)
- [TypeScript Calculator](./samples/typescript/README.md)
- [Python Calculator](./samples/python/)

## Recursos Adicionales

- [Build Agents using Model Context Protocol on Azure](https://learn.microsoft.com/azure/developer/ai/intro-agents-mcp)
- [Remote MCP with Azure Container Apps (Node.js/TypeScript/JavaScript)](https://learn.microsoft.com/samples/azure-samples/mcp-container-ts/mcp-container-ts/)
- [.NET OpenAI MCP Agent](https://learn.microsoft.com/samples/azure-samples/openai-mcp-agent-dotnet/openai-mcp-agent-dotnet/)

## Qué sigue

Comienza con la primera lección: [Creando tu primer Servidor MCP](01-first-server/README.md)

Una vez que hayas completado este módulo, continúa con: [Módulo 4: Implementación Práctica](../04-PracticalImplementation/README.md)
