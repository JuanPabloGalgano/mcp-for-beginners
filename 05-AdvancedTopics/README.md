# Temas Avanzados en MCP

[![Advanced MCP: Secure, Scalable, and Multi-modal AI Agents](../images/video-thumbnails/06.png)](https://youtu.be/4yjmGvJzYdY)

_(Haz clic en la imagen de arriba para ver el video de esta lección)_

Este capítulo cubre una serie de temas avanzados en la implementación del Protocolo de Contexto de Modelos (MCP), incluyendo integración multimodal, escalabilidad, mejores prácticas de seguridad e integración empresarial. Estos temas son cruciales para construir aplicaciones MCP robustas y listas para producción que puedan satisfacer las demandas de los sistemas de IA modernos.

## Descripción General

Esta lección explora conceptos avanzados en la implementación del Protocolo de Contexto de Modelos, con enfoque en la integración multimodal, escalabilidad, mejores prácticas de seguridad e integración empresarial. Estos temas son esenciales para construir aplicaciones MCP de nivel de producción que puedan manejar requisitos complejos en entornos empresariales.

## Objetivos de Aprendizaje

Al final de esta lección, serás capaz de:

- Implementar capacidades multimodales dentro de los marcos MCP
- Diseñar arquitecturas MCP escalables para escenarios de alta demanda
- Aplicar mejores prácticas de seguridad alineadas con los principios de seguridad de MCP
- Integrar MCP con sistemas y marcos de IA empresariales
- Optimizar el rendimiento y la confiabilidad en entornos de producción

## Lecciones y Proyectos de Muestra

| Enlace | Título | Descripción |
|------|-------|-------------|
| [5.1 Integration with Azure](./mcp-integration/README.md) | Integración con Azure | Aprende cómo integrar tu servidor MCP en Azure |
| [5.2 Multi modal sample](./mcp-multi-modality/README.md) | Muestras multimodales de MCP  | Muestras de respuestas de audio, imagen y multimodal |
| [5.3 MCP OAuth2 sample](./mcp-oauth2-demo/) | Demo de MCP OAuth2 | Aplicación mínima de Spring Boot que muestra OAuth2 con MCP, tanto como Servidor de Autorización como de Recursos. Demuestra la emisión segura de tokens, endpoints protegidos, despliegue en Azure Container Apps e integración de API Management. |
| [5.4 Root Contexts](./mcp-root-contexts/README.md) | Contextos raíz  | Aprende más sobre el contexto raíz y cómo implementarlos |
| [5.5 Routing](./mcp-routing/README.md) | Enrutamiento | Aprende los diferentes tipos de enrutamiento |
| [5.6 Sampling](./mcp-sampling/README.md) | Muestreo | Aprende cómo trabajar con el muestreo |
| [5.7 Scaling](./mcp-scaling/README.md) | Escalado  | Aprende sobre escalado |
| [5.8 Security](./mcp-security/README.md) | Seguridad  | Asegura tu servidor MCP |
| [5.9 Web Search sample](./web-search-mcp/README.md) | MCP de Búsqueda Web | Servidor y cliente MCP en Python que se integra con SerpAPI para búsqueda web en tiempo real, noticias, productos y preguntas y respuestas. Demuestra la orquestación de múltiples herramientas, integración de API externa y manejo robusto de errores. |
| [5.10 Realtime Streaming](./mcp-realtimestreaming/README.md) | Streaming  | La transmisión de datos en tiempo real se ha vuelto esencial en el mundo actual impulsado por datos, donde las empresas y aplicaciones requieren acceso inmediato a la información para tomar decisiones oportunas.|
| [5.11 Realtime Web Search](./mcp-realtimesearch/README.md) | Búsqueda Web | Búsqueda web en tiempo real: cómo MCP transforma la búsqueda web en tiempo real proporcionando un enfoque estandarizado para la gestión de contexto entre modelos de IA, motores de búsqueda y aplicaciones.|
| [5.12  Entra ID Authentication for Model Context Protocol Servers](./mcp-security-entra/README.md) | Autenticación con Entra ID | Microsoft Entra ID proporciona una solución robusta de gestión de identidades y accesos basada en la nube, ayudando a garantizar que solo los usuarios y aplicaciones autorizados puedan interactuar con tu servidor MCP.|
| [5.13 Azure AI Foundry Agent Integration](./mcp-foundry-agent-integration/README.md) | Integración con Azure AI Foundry | Aprende cómo integrar servidores del Protocolo de Contexto de Modelos con agentes de Azure AI Foundry, habilitando una poderosa orquestación de herramientas y capacidades de IA empresarial con conexiones estandarizadas a fuentes de datos externas.|
| [5.14 Context Engineering](./mcp-contextengineering/README.md) | Ingeniería de Contexto | La oportunidad futura de las técnicas de ingeniería de contexto para servidores MCP, incluyendo optimización de contexto, gestión dinámica de contexto y estrategias para una ingeniería de prompts efectiva dentro de los marcos MCP.|
| [5.15 MCP Custom Transport](./mcp-transport/README.md) | Transporte Personalizado | Aprende cómo implementar mecanismos de transporte personalizados para escenarios especializados de comunicación MCP.|
| [5.16 Protocol Features Deep Dive](./mcp-protocol-features/README.md) | Características del Protocolo | Domina las características avanzadas del protocolo incluyendo notificaciones de progreso, cancelación de solicitudes, plantillas de recursos y patrones de manejo de errores.|

> **Novedades en la Especificación MCP 2025-11-25**: La especificación ahora incluye soporte experimental para **Tasks** (operaciones de larga duración con seguimiento de progreso), **Tool Annotations** (metadatos sobre el comportamiento de herramientas para mayor seguridad), **URL Mode Elicitation** (solicitud de contenido de URL específico desde clientes) y **Roots** mejorado (para gestión del contexto del espacio de trabajo). Consulta el [registro de cambios de la Especificación MCP](https://spec.modelcontextprotocol.io/) para todos los detalles.

## Referencias Adicionales

Para obtener la información más actualizada sobre temas avanzados de MCP, consulta:
- [MCP Documentation](https://modelcontextprotocol.io/)
- [MCP Specification (2025-11-25)](https://spec.modelcontextprotocol.io/specification/2025-11-25/)
- [GitHub Repository](https://github.com/modelcontextprotocol)
- [OWASP MCP Top 10](https://microsoft.github.io/mcp-azure-security-guide/mcp/) - Riesgos de seguridad y mitigaciones
- [MCP Security Summit Workshop (Sherpa)](https://azure-samples.github.io/sherpa/) - Entrenamiento práctico de seguridad

## Conclusiones Clave

- Las implementaciones MCP multimodales amplían las capacidades de IA más allá del procesamiento de texto
- La escalabilidad es esencial para los despliegues empresariales y puede abordarse mediante escalado horizontal y vertical
- Las medidas de seguridad integrales protegen los datos y garantizan un control de acceso adecuado
- La integración empresarial con plataformas como Azure OpenAI y Microsoft AI Foundry mejora las capacidades de MCP
- Las implementaciones avanzadas de MCP se benefician de arquitecturas optimizadas y una gestión cuidadosa de los recursos

## Ejercicio

Diseña una implementación MCP de nivel empresarial para un caso de uso específico:

1. Identifica los requisitos multimodales para tu caso de uso
2. Describe los controles de seguridad necesarios para proteger los datos sensibles
3. Diseña una arquitectura escalable que pueda manejar cargas variables
4. Planifica los puntos de integración con los sistemas de IA empresariales
5. Documenta los posibles cuellos de botella de rendimiento y las estrategias de mitigación

## Recursos Adicionales

- [Azure OpenAI Documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/)
- [Microsoft AI Foundry Documentation](https://learn.microsoft.com/en-us/ai-services/)

---

## Qué sigue

Explora las lecciones de este módulo comenzando con: [5.1 MCP Integration](./mcp-integration/README.md)

Una vez que hayas completado este módulo, continúa con: [Módulo 6: Contribuciones de la Comunidad](../06-CommunityContributions/README.md)
