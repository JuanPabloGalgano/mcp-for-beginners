# Seguridad en MCP: Protección Integral para Sistemas de IA

[![MCP Security Best Practices](../images/video-thumbnails/03.png)](https://youtu.be/88No8pw706o)

_(Haz clic en la imagen de arriba para ver el video de esta lección)_

La seguridad es fundamental en el diseño de sistemas de IA, por eso la priorizamos como nuestra segunda sección. Esto se alinea con el principio **Secure by Design** de Microsoft del [Secure Future Initiative](https://www.microsoft.com/security/blog/2025/04/17/microsofts-secure-by-design-journey-one-year-of-success/).

El Model Context Protocol (MCP) aporta nuevas y poderosas capacidades a las aplicaciones impulsadas por IA, al tiempo que introduce desafíos de seguridad únicos que van más allá de los riesgos tradicionales del software. Los sistemas MCP enfrentan tanto preocupaciones de seguridad establecidas (codificación segura, mínimo privilegio, seguridad de la cadena de suministro) como nuevas amenazas específicas de IA, incluyendo inyección de prompts, envenenamiento de herramientas, secuestro de sesiones, ataques de proxy confuso, vulnerabilidades de reenvío de tokens y modificación dinámica de capacidades.

Esta lección explora los riesgos de seguridad más críticos en las implementaciones de MCP, abarcando autenticación, autorización, permisos excesivos, inyección indirecta de prompts, seguridad de sesiones, problemas de proxy confuso, gestión de tokens y vulnerabilidades en la cadena de suministro. Aprenderás controles prácticos y mejores prácticas para mitigar estos riesgos, aprovechando soluciones de Microsoft como Prompt Shields, Azure Content Safety y GitHub Advanced Security para fortalecer tu despliegue de MCP.

## Objetivos de Aprendizaje

Al finalizar esta lección, podrás:

- **Identificar Amenazas Específicas de MCP**: Reconocer los riesgos de seguridad únicos en los sistemas MCP, incluyendo inyección de prompts, envenenamiento de herramientas, permisos excesivos, secuestro de sesiones, problemas de proxy confuso, vulnerabilidades de reenvío de tokens y riesgos en la cadena de suministro
- **Aplicar Controles de Seguridad**: Implementar mitigaciones efectivas como autenticación robusta, acceso con mínimo privilegio, gestión segura de tokens, controles de seguridad de sesiones y verificación de la cadena de suministro
- **Aprovechar las Soluciones de Seguridad de Microsoft**: Entender y desplegar Microsoft Prompt Shields, Azure Content Safety y GitHub Advanced Security para la protección de cargas de trabajo MCP
- **Validar la Seguridad de las Herramientas**: Reconocer la importancia de la validación de metadatos de herramientas, el monitoreo de cambios dinámicos y la defensa contra ataques de inyección indirecta de prompts
- **Integrar Mejores Prácticas**: Combinar los fundamentos de seguridad establecidos (codificación segura, endurecimiento de servidores, confianza cero) con controles específicos de MCP para una protección integral

# Arquitectura y Controles de Seguridad de MCP

Las implementaciones modernas de MCP requieren enfoques de seguridad por capas que aborden tanto la seguridad tradicional del software como las amenazas específicas de IA. La especificación MCP, en rápida evolución, continúa madurando sus controles de seguridad, permitiendo una mejor integración con las arquitecturas de seguridad empresariales y las mejores prácticas establecidas.

La investigación del [Microsoft Digital Defense Report](https://aka.ms/mddr) demuestra que **el 98% de las brechas reportadas podrían prevenirse con una higiene de seguridad robusta**. La estrategia de protección más efectiva combina prácticas de seguridad fundamentales con controles específicos de MCP; las medidas de seguridad base probadas siguen siendo las más impactantes para reducir el riesgo de seguridad general.

## Panorama Actual de Seguridad

> **Nota:** Esta información refleja los estándares de seguridad de MCP a partir del **5 de febrero de 2026**, alineados con la **Especificación MCP 2025-11-25**. El protocolo MCP continúa evolucionando rápidamente y las implementaciones futuras pueden introducir nuevos patrones de autenticación y controles mejorados. Consulta siempre la [Especificación MCP](https://spec.modelcontextprotocol.io/) actual, el [repositorio de GitHub de MCP](https://github.com/modelcontextprotocol) y la [documentación de mejores prácticas de seguridad](https://modelcontextprotocol.io/specification/2025-11-25/basic/security_best_practices) para obtener la guía más reciente.

## 🏔️ Taller MCP Security Summit (Sherpa)

Para **entrenamiento práctico de seguridad**, recomendamos ampliamente el **Taller MCP Security Summit** (Sherpa), una expedición guiada y completa para asegurar servidores MCP en Microsoft Azure.

### Descripción General del Taller

El [Taller MCP Security Summit](https://azure-samples.github.io/sherpa/) proporciona entrenamiento práctico y aplicable mediante una metodología probada de "vulnerable → explotar → corregir → validar". Podrás:

- **Aprender Rompiendo Cosas**: Experimenta las vulnerabilidades de primera mano explotando servidores intencionalmente inseguros
- **Usar Seguridad Nativa de Azure**: Aprovecha Azure Entra ID, Key Vault, API Management y AI Content Safety
- **Seguir la Defensa en Profundidad**: Avanza por campamentos construyendo capas de seguridad integrales
- **Aplicar Estándares OWASP**: Cada técnica se asocia con la [Guía de Seguridad Azure OWASP MCP](https://microsoft.github.io/mcp-azure-security-guide/)
- **Obtener Código de Producción**: Termina con implementaciones funcionales y probadas

### La Ruta de la Expedición

| Campamento | Enfoque | Riesgos OWASP Cubiertos |
|------|-------|---------------------|
| **Campamento Base** | Fundamentos de MCP y vulnerabilidades de autenticación | MCP01, MCP07 |
| **Campamento 1: Identidad** | OAuth 2.1, Azure Managed Identity, Key Vault | MCP01, MCP02, MCP07 |
| **Campamento 2: Gateway** | API Management, Endpoints Privados, gobernanza | MCP02, MCP07, MCP09 |
| **Campamento 3: Seguridad de E/S** | Inyección de prompts, protección de PII, seguridad de contenido | MCP03, MCP05, MCP06 |
| **Campamento 4: Monitoreo** | Log Analytics, dashboards, detección de amenazas | MCP08 |
| **La Cumbre** | Prueba de integración Red Team / Blue Team | Todos |

**Comienza aquí**: [https://azure-samples.github.io/sherpa/](https://azure-samples.github.io/sherpa/)

## OWASP MCP Top 10 Riesgos de Seguridad

La [Guía de Seguridad Azure OWASP MCP](https://microsoft.github.io/mcp-azure-security-guide/) detalla los diez riesgos de seguridad más críticos para las implementaciones de MCP:

| Riesgo | Descripción | Mitigación en Azure |
|------|-------------|------------------|
| **MCP01** | Gestión incorrecta de tokens y exposición de secretos | Azure Key Vault, Managed Identity |
| **MCP02** | Escalada de privilegios por expansión de alcance | RBAC, Acceso Condicional |
| **MCP03** | Envenenamiento de herramientas | Validación de herramientas, verificación de integridad |
| **MCP04** | Ataques a la cadena de suministro | GitHub Advanced Security, escaneo de dependencias |
| **MCP05** | Inyección y ejecución de comandos | Validación de entrada, sandboxing |
| **MCP06** | Inyección de prompts mediante cargas contextuales | Azure AI Content Safety, Prompt Shields |
| **MCP07** | Autenticación y autorización insuficientes | Azure Entra ID, OAuth 2.1 con PKCE |
| **MCP08** | Falta de auditoría y telemetría | Azure Monitor, Application Insights |
| **MCP09** | Servidores MCP en la sombra | Gobernanza del API Center, aislamiento de red |
| **MCP10** | Inyección de contexto y sobreexposición | Clasificación de datos, exposición mínima |

### Evolución de la Autenticación en MCP

La especificación MCP ha evolucionado significativamente en su enfoque de autenticación y autorización:

- **Enfoque Original**: Las especificaciones tempranas requerían que los desarrolladores implementaran servidores de autenticación personalizados, con los servidores MCP actuando como Servidores de Autorización OAuth 2.0 gestionando la autenticación de usuarios directamente
- **Estándar Actual (2025-11-25)**: La especificación actualizada permite que los servidores MCP deleguen la autenticación a proveedores de identidad externos (como Microsoft Entra ID), mejorando la postura de seguridad y reduciendo la complejidad de implementación
- **Seguridad en la Capa de Transporte**: Soporte mejorado para mecanismos de transporte seguro con patrones de autenticación apropiados tanto para conexiones locales (STDIO) como remotas (Streamable HTTP)

## Seguridad en Autenticación y Autorización

### Desafíos Actuales de Seguridad

Las implementaciones modernas de MCP enfrentan varios desafíos de autenticación y autorización:

### Riesgos y Vectores de Amenaza

- **Lógica de Autorización Mal Configurada**: Una implementación de autorización defectuosa en los servidores MCP puede exponer datos sensibles y aplicar controles de acceso incorrectamente
- **Compromiso de Tokens OAuth**: El robo de tokens de servidores MCP locales permite a los atacantes suplantar servidores y acceder a servicios aguas abajo
- **Vulnerabilidades de Reenvío de Tokens**: El manejo inadecuado de tokens crea omisiones de controles de seguridad y brechas de responsabilidad
- **Permisos Excesivos**: Los servidores MCP con exceso de privilegios violan el principio de mínimo privilegio y amplían la superficie de ataque

#### Reenvío de Tokens: Un Antipatrón Crítico

**El reenvío de tokens está explícitamente prohibido** en la especificación de autorización actual de MCP debido a sus graves implicaciones de seguridad:

##### Elusión de Controles de Seguridad
- Los servidores MCP y las APIs aguas abajo implementan controles de seguridad críticos (limitación de velocidad, validación de solicitudes, monitoreo de tráfico) que dependen de la validación adecuada de tokens
- El uso directo de tokens del cliente hacia la API omite estas protecciones esenciales, socavando la arquitectura de seguridad

##### Desafíos de Responsabilidad y Auditoría
- Los servidores MCP no pueden distinguir entre clientes que usan tokens emitidos aguas arriba, rompiendo las pistas de auditoría
- Los registros del servidor de recursos aguas abajo muestran orígenes de solicitudes engañosos en lugar de los intermediarios reales del servidor MCP
- La investigación de incidentes y la auditoría de cumplimiento se vuelven significativamente más difíciles

##### Riesgos de Exfiltración de Datos
- Las afirmaciones de tokens no validadas permiten a actores maliciosos con tokens robados usar los servidores MCP como proxies para la exfiltración de datos
- Las violaciones de los límites de confianza permiten patrones de acceso no autorizados que eluden los controles de seguridad previstos

##### Vectores de Ataque Multi-Servicio
- Los tokens comprometidos aceptados por múltiples servicios permiten el movimiento lateral entre sistemas conectados
- Las suposiciones de confianza entre servicios pueden violarse cuando no se puede verificar el origen del token

### Controles y Mitigaciones de Seguridad

**Requisitos Críticos de Seguridad:**

> **OBLIGATORIO**: Los servidores MCP **NO DEBEN** aceptar tokens que no hayan sido emitidos explícitamente para el servidor MCP

#### Controles de Autenticación y Autorización

- **Revisión Rigurosa de Autorización**: Realiza auditorías exhaustivas de la lógica de autorización del servidor MCP para garantizar que solo los usuarios y clientes previstos puedan acceder a los recursos sensibles
  - **Guía de Implementación**: [Azure API Management as Authentication Gateway for MCP Servers](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)
  - **Integración de Identidad**: [Using Microsoft Entra ID for MCP Server Authentication](https://den.dev/blog/mcp-server-auth-entra-id-session/)

- **Gestión Segura de Tokens**: Implementa las [mejores prácticas de validación y ciclo de vida de tokens de Microsoft](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens)
  - Valida que las afirmaciones de audiencia del token coincidan con la identidad del servidor MCP
  - Implementa políticas adecuadas de rotación y expiración de tokens
  - Previene ataques de repetición de tokens y uso no autorizado

- **Almacenamiento Protegido de Tokens**: Almacenamiento seguro de tokens con cifrado tanto en reposo como en tránsito
  - **Mejores Prácticas**: [Secure Token Storage and Encryption Guidelines](https://youtu.be/uRdX37EcCwg?si=6fSChs1G4glwXRy2)

#### Implementación de Control de Acceso

- **Principio de Mínimo Privilegio**: Otorga a los servidores MCP solo los permisos mínimos necesarios para la funcionalidad prevista
  - Revisiones y actualizaciones periódicas de permisos para prevenir la expansión de privilegios
  - **Documentación de Microsoft**: [Secure Least-Privileged Access](https://learn.microsoft.com/entra/identity-platform/secure-least-privileged-access)

- **Control de Acceso Basado en Roles (RBAC)**: Implementa asignaciones de roles con granularidad fina
  - Delimita los roles específicamente a recursos y acciones concretas
  - Evita permisos amplios o innecesarios que amplíen la superficie de ataque

- **Monitoreo Continuo de Permisos**: Implementa auditoría y monitoreo continuo del acceso
  - Monitorea patrones de uso de permisos en busca de anomalías
  - Remedia rápidamente los privilegios excesivos o no utilizados

## Amenazas de Seguridad Específicas de IA

### Inyección de Prompts y Ataques de Manipulación de Herramientas

Las implementaciones modernas de MCP enfrentan vectores de ataque sofisticados específicos de IA que las medidas de seguridad tradicionales no pueden abordar completamente:

#### **Inyección Indirecta de Prompts (Inyección de Prompts entre Dominios)**

La **Inyección Indirecta de Prompts** representa una de las vulnerabilidades más críticas en los sistemas de IA habilitados para MCP. Los atacantes incrustan instrucciones maliciosas dentro de contenido externo (documentos, páginas web, correos electrónicos o fuentes de datos) que los sistemas de IA procesan posteriormente como comandos legítimos.

**Escenarios de Ataque:**
- **Inyección basada en documentos**: Instrucciones maliciosas ocultas en documentos procesados que desencadenan acciones de IA no deseadas
- **Explotación de contenido web**: Páginas web comprometidas que contienen prompts incrustados que manipulan el comportamiento de la IA cuando se rastrean
- **Ataques basados en correo electrónico**: Prompts maliciosos en correos electrónicos que causan que los asistentes de IA filtren información o realicen acciones no autorizadas
- **Contaminación de fuentes de datos**: Bases de datos o APIs comprometidas que sirven contenido adulterado a los sistemas de IA

**Impacto en el Mundo Real**: Estos ataques pueden resultar en exfiltración de datos, violaciones de privacidad, generación de contenido dañino y manipulación de interacciones de usuarios. Para un análisis detallado, consulta [Prompt Injection in MCP (Simon Willison)](https://simonwillison.net/2025/Apr/9/mcp-prompt-injection/).

![Prompt Injection Attack Diagram](../images/02-Security/prompt-injection.png)

#### **Ataques de Envenenamiento de Herramientas**

El **Envenenamiento de Herramientas** tiene como objetivo los metadatos que definen las herramientas MCP, explotando cómo los LLMs interpretan las descripciones y parámetros de las herramientas para tomar decisiones de ejecución.

**Mecanismos de Ataque:**
- **Manipulación de Metadatos**: Los atacantes inyectan instrucciones maliciosas en descripciones de herramientas, definiciones de parámetros o ejemplos de uso
- **Instrucciones Invisibles**: Prompts ocultos en los metadatos de las herramientas que son procesados por los modelos de IA pero invisibles para los usuarios humanos
- **Modificación Dinámica de Herramientas ("Rug Pulls")**: Las herramientas aprobadas por los usuarios son modificadas posteriormente para realizar acciones maliciosas sin el conocimiento del usuario
- **Inyección de Parámetros**: Contenido malicioso incrustado en los esquemas de parámetros de herramientas que influye en el comportamiento del modelo

**Riesgos de Servidores Alojados**: Los servidores MCP remotos presentan riesgos elevados ya que las definiciones de herramientas pueden actualizarse después de la aprobación inicial del usuario, creando escenarios donde herramientas previamente seguras se vuelven maliciosas. Para un análisis completo, consulta [Tool Poisoning Attacks (Invariant Labs)](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks).

![Tool Injection Attack Diagram](../images/02-Security/tool-injection.png)

#### **Vectores de Ataque Adicionales de IA**

- **Inyección de Prompts entre Dominios (XPIA)**: Ataques sofisticados que aprovechan contenido de múltiples dominios para eludir los controles de seguridad
- **Modificación Dinámica de Capacidades**: Cambios en tiempo real en las capacidades de las herramientas que escapan a las evaluaciones de seguridad iniciales
- **Envenenamiento de Ventana de Contexto**: Ataques que manipulan grandes ventanas de contexto para ocultar instrucciones maliciosas
- **Ataques de Confusión del Modelo**: Explotación de las limitaciones del modelo para crear comportamientos impredecibles o inseguros


### Impacto de los Riesgos de Seguridad de IA

**Consecuencias de Alto Impacto:**
- **Exfiltración de Datos**: Acceso no autorizado y robo de datos empresariales o personales sensibles
- **Violaciones de Privacidad**: Exposición de información de identificación personal (PII) y datos confidenciales del negocio
- **Manipulación del Sistema**: Modificaciones no deseadas de sistemas y flujos de trabajo críticos
- **Robo de Credenciales**: Compromiso de tokens de autenticación y credenciales de servicio
- **Movimiento Lateral**: Uso de sistemas de IA comprometidos como pivotes para ataques más amplios en la red

### Soluciones de Seguridad de IA de Microsoft

#### **AI Prompt Shields: Protección Avanzada contra Ataques de Inyección**

Microsoft **AI Prompt Shields** proporciona una defensa integral contra ataques de inyección de prompts tanto directos como indirectos a través de múltiples capas de seguridad:

##### **Mecanismos de Protección Principales:**

1. **Detección y Filtrado Avanzado**
   - Algoritmos de aprendizaje automático y técnicas de NLP detectan instrucciones maliciosas en contenido externo
   - Análisis en tiempo real de documentos, páginas web, correos electrónicos y fuentes de datos en busca de amenazas incrustadas
   - Comprensión contextual de patrones de prompts legítimos vs. maliciosos

2. **Técnicas de Destacado**
   - Distingue entre instrucciones del sistema de confianza y entradas externas potencialmente comprometidas
   - Métodos de transformación de texto que mejoran la relevancia del modelo mientras aíslan el contenido malicioso
   - Ayuda a los sistemas de IA a mantener la jerarquía adecuada de instrucciones e ignorar comandos inyectados

3. **Sistemas de Delimitadores y Marcado de Datos**
   - Definición explícita de límites entre mensajes del sistema de confianza y texto de entrada externo
   - Marcadores especiales que resaltan los límites entre fuentes de datos de confianza y no confiables
   - La separación clara previene la confusión de instrucciones y la ejecución de comandos no autorizados

4. **Inteligencia de Amenazas Continua**
   - Microsoft monitorea continuamente los patrones de ataque emergentes y actualiza las defensas
   - Búsqueda proactiva de amenazas para nuevas técnicas de inyección y vectores de ataque
   - Actualizaciones regulares del modelo de seguridad para mantener la efectividad frente a amenazas en evolución

5. **Integración con Azure Content Safety**
   - Parte de la suite integral de Azure AI Content Safety
   - Detección adicional de intentos de jailbreak, contenido dañino y violaciones de políticas de seguridad
   - Controles de seguridad unificados en todos los componentes de la aplicación de IA

**Recursos de Implementación**: [Microsoft Prompt Shields Documentation](https://learn.microsoft.com/azure/ai-services/content-safety/concepts/jailbreak-detection)

![Microsoft Prompt Shields Protection](../images/02-Security/prompt-shield.png)


## Amenazas Avanzadas de Seguridad en MCP

### Vulnerabilidades de Secuestro de Sesiones

El **secuestro de sesiones** representa un vector de ataque crítico en las implementaciones MCP con estado, donde partes no autorizadas obtienen y abusan de identificadores de sesión legítimos para suplantar clientes y realizar acciones no autorizadas.

#### **Escenarios de Ataque y Riesgos**

- **Inyección de Prompts mediante Secuestro de Sesión**: Los atacantes con IDs de sesión robados inyectan eventos maliciosos en servidores que comparten el estado de la sesión, potencialmente desencadenando acciones dañinas o accediendo a datos sensibles
- **Suplantación Directa**: Los IDs de sesión robados permiten llamadas directas al servidor MCP que eluden la autenticación, tratando a los atacantes como usuarios legítimos
- **Flujos Reanudables Comprometidos**: Los atacantes pueden terminar solicitudes prematuramente, haciendo que los clientes legítimos reanuden con contenido potencialmente malicioso

#### **Controles de Seguridad para la Gestión de Sesiones**

**Requisitos Críticos:**
- **Verificación de Autorización**: Los servidores MCP que implementan autorización **DEBEN** verificar TODAS las solicitudes entrantes y **NO DEBEN** depender de las sesiones para la autenticación
- **Generación Segura de Sesiones**: Usa IDs de sesión criptográficamente seguros y no deterministas generados con generadores de números aleatorios seguros
- **Vinculación Específica del Usuario**: Vincula los IDs de sesión a información específica del usuario usando formatos como `<user_id>:<session_id>` para prevenir el abuso de sesiones entre usuarios
- **Gestión del Ciclo de Vida de la Sesión**: Implementa expiración, rotación e invalidación adecuadas para limitar las ventanas de vulnerabilidad
- **Seguridad del Transporte**: HTTPS obligatorio para todas las comunicaciones para prevenir la interceptación de IDs de sesión

### Problema del Proxy Confuso

El **problema del proxy confuso** ocurre cuando los servidores MCP actúan como proxies de autenticación entre clientes y servicios de terceros, creando oportunidades para la elusión de autorización mediante la explotación de IDs de cliente estáticos.

#### **Mecánica del Ataque y Riesgos**

- **Elusión de Consentimiento basada en Cookies**: La autenticación previa del usuario crea cookies de consentimiento que los atacantes explotan mediante solicitudes de autorización maliciosas con URIs de redirección manipulados
- **Robo de Código de Autorización**: Las cookies de consentimiento existentes pueden hacer que los servidores de autorización omitan las pantallas de consentimiento, redirigiendo los códigos a endpoints controlados por atacantes
- **Acceso No Autorizado a la API**: Los códigos de autorización robados permiten el intercambio de tokens y la suplantación de usuarios sin aprobación explícita

#### **Estrategias de Mitigación**

**Controles Obligatorios:**
- **Requisitos de Consentimiento Explícito**: Los servidores proxy MCP que usan IDs de cliente estáticos **DEBEN** obtener el consentimiento del usuario para cada cliente registrado dinámicamente
- **Implementación de Seguridad OAuth 2.1**: Sigue las mejores prácticas de seguridad actuales de OAuth, incluyendo PKCE (Proof Key for Code Exchange) para todas las solicitudes de autorización
- **Validación Estricta del Cliente**: Implementa una validación rigurosa de los URIs de redirección e identificadores de cliente para prevenir la explotación

### Vulnerabilidades de Reenvío de Tokens

El **reenvío de tokens** representa un antipatrón explícito donde los servidores MCP aceptan tokens de clientes sin la validación adecuada y los reenvían a APIs aguas abajo, violando las especificaciones de autorización de MCP.

#### **Implicaciones de Seguridad**

- **Elusión de Controles**: El uso directo de tokens del cliente hacia la API omite controles críticos de limitación de velocidad, validación y monitoreo
- **Corrupción de la Pista de Auditoría**: Los tokens emitidos aguas arriba hacen imposible la identificación del cliente, rompiendo las capacidades de investigación de incidentes
- **Exfiltración de Datos mediante Proxy**: Los tokens no validados permiten a actores maliciosos usar los servidores como proxies para acceso no autorizado a datos
- **Violaciones de los Límites de Confianza**: Las suposiciones de confianza de los servicios aguas abajo pueden violarse cuando no se puede verificar el origen del token
- **Expansión de Ataques Multi-Servicio**: Los tokens comprometidos aceptados en múltiples servicios permiten el movimiento lateral

#### **Controles de Seguridad Requeridos**

**Requisitos No Negociables:**
- **Validación de Tokens**: Los servidores MCP **NO DEBEN** aceptar tokens que no hayan sido emitidos explícitamente para el servidor MCP
- **Verificación de Audiencia**: Siempre valida que las afirmaciones de audiencia del token coincidan con la identidad del servidor MCP
- **Ciclo de Vida Adecuado del Token**: Implementa tokens de acceso de corta duración con prácticas de rotación segura


## Seguridad de la Cadena de Suministro para Sistemas de IA

La seguridad de la cadena de suministro ha evolucionado más allá de las dependencias tradicionales de software para abarcar todo el ecosistema de IA. Las implementaciones modernas de MCP deben verificar y monitorear rigurosamente todos los componentes relacionados con IA, ya que cada uno introduce vulnerabilidades potenciales que podrían comprometer la integridad del sistema.

### Componentes Ampliados de la Cadena de Suministro de IA

**Dependencias Tradicionales de Software:**
- Bibliotecas y frameworks de código abierto
- Imágenes de contenedores y sistemas base
- Herramientas de desarrollo y pipelines de compilación
- Componentes y servicios de infraestructura

**Elementos Específicos de la Cadena de Suministro de IA:**
- **Modelos de Base**: Modelos preentrenados de varios proveedores que requieren verificación de procedencia
- **Servicios de Embeddings**: Servicios externos de vectorización y búsqueda semántica
- **Proveedores de Contexto**: Fuentes de datos, bases de conocimiento y repositorios de documentos
- **APIs de Terceros**: Servicios externos de IA, pipelines de ML y endpoints de procesamiento de datos
- **Artefactos de Modelos**: Pesos, configuraciones y variantes de modelos ajustados
- **Fuentes de Datos de Entrenamiento**: Conjuntos de datos utilizados para el entrenamiento y ajuste fino de modelos

### Estrategia Integral de Seguridad de la Cadena de Suministro

#### **Verificación y Confianza de Componentes**
- **Validación de Procedencia**: Verifica el origen, la licencia y la integridad de todos los componentes de IA antes de la integración
- **Evaluación de Seguridad**: Realiza escaneos de vulnerabilidades y revisiones de seguridad para modelos, fuentes de datos y servicios de IA
- **Análisis de Reputación**: Evalúa el historial de seguridad y las prácticas de los proveedores de servicios de IA
- **Verificación de Cumplimiento**: Asegura que todos los componentes cumplan con los requisitos de seguridad y regulatorios de la organización

#### **Pipelines de Despliegue Seguro**
- **Seguridad Automatizada de CI/CD**: Integra el escaneo de seguridad a lo largo de los pipelines de despliegue automatizados
- **Integridad de Artefactos**: Implementa verificación criptográfica para todos los artefactos desplegados (código, modelos, configuraciones)
- **Despliegue por Etapas**: Usa estrategias de despliegue progresivo con validación de seguridad en cada etapa
- **Repositorios de Artefactos de Confianza**: Despliega solo desde registros y repositorios de artefactos verificados y seguros

#### **Monitoreo Continuo y Respuesta**
- **Escaneo de Dependencias**: Monitoreo continuo de vulnerabilidades para todas las dependencias de software y componentes de IA
- **Monitoreo de Modelos**: Evaluación continua del comportamiento, la deriva del rendimiento y las anomalías de seguridad del modelo
- **Seguimiento del Estado del Servicio**: Monitorea los servicios de IA externos para detectar disponibilidad, incidentes de seguridad y cambios de política
- **Integración de Inteligencia de Amenazas**: Incorpora feeds de amenazas específicos para los riesgos de seguridad de IA y ML

#### **Control de Acceso y Mínimo Privilegio**
- **Permisos a Nivel de Componente**: Restringe el acceso a modelos, datos y servicios según la necesidad del negocio
- **Gestión de Cuentas de Servicio**: Implementa cuentas de servicio dedicadas con los permisos mínimos necesarios
- **Segmentación de Red**: Aísla los componentes de IA y limita el acceso en red entre servicios
- **Controles del Gateway de API**: Usa gateways de API centralizados para controlar y monitorear el acceso a los servicios externos de IA

#### **Respuesta a Incidentes y Recuperación**
- **Procedimientos de Respuesta Rápida**: Procesos establecidos para parchear o reemplazar componentes de IA comprometidos
- **Rotación de Credenciales**: Sistemas automatizados para rotar secretos, claves de API y credenciales de servicio
- **Capacidades de Reversión**: Capacidad para revertir rápidamente a versiones anteriores conocidas como buenas de los componentes de IA
- **Recuperación ante Brechas en la Cadena de Suministro**: Procedimientos específicos para responder a compromisos de servicios de IA aguas arriba

### Herramientas e Integración de Seguridad de Microsoft

**GitHub Advanced Security** proporciona protección integral de la cadena de suministro incluyendo:
- **Escaneo de Secretos**: Detección automatizada de credenciales, claves de API y tokens en repositorios
- **Escaneo de Dependencias**: Evaluación de vulnerabilidades para dependencias y bibliotecas de código abierto
- **Análisis CodeQL**: Análisis de código estático para vulnerabilidades de seguridad y problemas de codificación
- **Información de la Cadena de Suministro**: Visibilidad sobre el estado y la seguridad de las dependencias

**Integración con Azure DevOps y Azure Repos:**
- Integración de escaneo de seguridad sin interrupciones en las plataformas de desarrollo de Microsoft
- Verificaciones de seguridad automatizadas en Azure Pipelines para cargas de trabajo de IA
- Aplicación de políticas para el despliegue seguro de componentes de IA

**Prácticas Internas de Microsoft:**
Microsoft implementa extensas prácticas de seguridad en la cadena de suministro en todos sus productos. Conoce los enfoques probados en [The Journey to Secure the Software Supply Chain at Microsoft](https://devblogs.microsoft.com/engineering-at-microsoft/the-journey-to-secure-the-software-supply-chain-at-microsoft/).


## Mejores Prácticas Fundamentales de Seguridad

Las implementaciones de MCP heredan y se construyen sobre la postura de seguridad existente de tu organización. Fortalecer las prácticas de seguridad fundamentales mejora significativamente la seguridad general de los sistemas de IA y los despliegues de MCP.

### Fundamentos Principales de Seguridad

#### **Prácticas de Desarrollo Seguro**
- **Cumplimiento de OWASP**: Protege contra las vulnerabilidades de [OWASP Top 10](https://owasp.org/www-project-top-ten/) para aplicaciones web
- **Protecciones Específicas de IA**: Implementa controles para [OWASP Top 10 for LLMs](https://genai.owasp.org/download/43299/?tmstv=1731900559)
- **Gestión Segura de Secretos**: Usa bóvedas dedicadas para tokens, claves de API y datos de configuración sensibles
- **Cifrado de Extremo a Extremo**: Implementa comunicaciones seguras en todos los componentes de la aplicación y flujos de datos
- **Validación de Entrada**: Validación rigurosa de todas las entradas de usuario, parámetros de API y fuentes de datos

#### **Endurecimiento de Infraestructura**
- **Autenticación Multifactor**: MFA obligatoria para todas las cuentas administrativas y de servicio
- **Gestión de Parches**: Parcheo automatizado y oportuno para sistemas operativos, frameworks y dependencias
- **Integración con Proveedor de Identidad**: Gestión centralizada de identidades a través de proveedores de identidad empresariales (Microsoft Entra ID, Active Directory)
- **Segmentación de Red**: Aislamiento lógico de los componentes MCP para limitar el potencial de movimiento lateral
- **Principio de Mínimo Privilegio**: Permisos mínimos requeridos para todos los componentes y cuentas del sistema

#### **Monitoreo y Detección de Seguridad**
- **Registro Integral**: Registro detallado de las actividades de la aplicación de IA, incluyendo las interacciones cliente-servidor de MCP
- **Integración con SIEM**: Gestión centralizada de información y eventos de seguridad para la detección de anomalías
- **Análisis de Comportamiento**: Monitoreo impulsado por IA para detectar patrones inusuales en el comportamiento del sistema y de los usuarios
- **Inteligencia de Amenazas**: Integración de feeds de amenazas externas e indicadores de compromiso (IOCs)
- **Respuesta a Incidentes**: Procedimientos bien definidos para la detección, respuesta y recuperación ante incidentes de seguridad

#### **Arquitectura de Confianza Cero**
- **Nunca Confiar, Siempre Verificar**: Verificación continua de usuarios, dispositivos y conexiones de red
- **Micro-Segmentación**: Controles de red granulares que aíslan cargas de trabajo y servicios individuales
- **Seguridad Centrada en la Identidad**: Políticas de seguridad basadas en identidades verificadas en lugar de la ubicación en la red
- **Evaluación Continua de Riesgos**: Evaluación dinámica de la postura de seguridad basada en el contexto y el comportamiento actuales
- **Acceso Condicional**: Controles de acceso que se adaptan en función de factores de riesgo, ubicación y confianza del dispositivo

### Patrones de Integración Empresarial

#### **Integración con el Ecosistema de Seguridad de Microsoft**
- **Microsoft Defender for Cloud**: Gestión integral de la postura de seguridad en la nube
- **Azure Sentinel**: Capacidades SIEM y SOAR nativas de la nube para la protección de cargas de trabajo de IA
- **Microsoft Entra ID**: Gestión de identidades y acceso empresarial con políticas de acceso condicional
- **Azure Key Vault**: Gestión centralizada de secretos con respaldo de módulo de seguridad de hardware (HSM)
- **Microsoft Purview**: Gobernanza de datos y cumplimiento para fuentes de datos de IA y flujos de trabajo

#### **Cumplimiento y Gobernanza**
- **Alineación Regulatoria**: Asegura que las implementaciones de MCP cumplan con los requisitos de cumplimiento específicos del sector (GDPR, HIPAA, SOC 2)
- **Clasificación de Datos**: Categorización y manejo adecuados de los datos sensibles procesados por los sistemas de IA
- **Pistas de Auditoría**: Registro integral para el cumplimiento regulatorio y la investigación forense
- **Controles de Privacidad**: Implementación de principios de privacidad por diseño en la arquitectura del sistema de IA
- **Gestión de Cambios**: Procesos formales para las revisiones de seguridad de las modificaciones del sistema de IA

Estas prácticas fundamentales crean una base sólida de seguridad que mejora la efectividad de los controles de seguridad específicos de MCP y proporciona una protección integral para las aplicaciones impulsadas por IA.

## Conclusiones Clave de Seguridad

- **Enfoque de Seguridad por Capas**: Combina prácticas de seguridad fundamentales (codificación segura, mínimo privilegio, verificación de la cadena de suministro, monitoreo continuo) con controles específicos de IA para una protección integral

- **Panorama de Amenazas Específicas de IA**: Los sistemas MCP enfrentan riesgos únicos incluyendo inyección de prompts, envenenamiento de herramientas, secuestro de sesiones, problemas de proxy confuso, vulnerabilidades de reenvío de tokens y permisos excesivos que requieren mitigaciones especializadas

- **Excelencia en Autenticación y Autorización**: Implementa autenticación robusta usando proveedores de identidad externos (Microsoft Entra ID), aplica la validación adecuada de tokens y nunca aceptes tokens que no hayan sido emitidos explícitamente para tu servidor MCP

- **Prevención de Ataques de IA**: Despliega Microsoft Prompt Shields y Azure Content Safety para defenderse contra inyección indirecta de prompts y ataques de envenenamiento de herramientas, mientras validas los metadatos de las herramientas y monitorizas los cambios dinámicos

- **Seguridad de Sesiones y Transporte**: Usa IDs de sesión criptográficamente seguros y no deterministas vinculados a las identidades de los usuarios, implementa una gestión adecuada del ciclo de vida de las sesiones y nunca uses las sesiones para la autenticación

- **Mejores Prácticas de Seguridad OAuth**: Previene ataques de proxy confuso mediante el consentimiento explícito del usuario para clientes registrados dinámicamente, implementación adecuada de OAuth 2.1 con PKCE y validación estricta del URI de redirección

- **Principios de Seguridad de Tokens**: Evita los antipatrones de reenvío de tokens, valida las afirmaciones de audiencia del token, implementa tokens de corta duración con rotación segura y mantén límites de confianza claros

- **Seguridad Integral de la Cadena de Suministro**: Trata todos los componentes del ecosistema de IA (modelos, embeddings, proveedores de contexto, APIs externas) con el mismo rigor de seguridad que las dependencias tradicionales de software

- **Evolución Continua**: Mantente actualizado con las especificaciones MCP en rápida evolución, contribuye a los estándares de la comunidad de seguridad y mantén posturas de seguridad adaptativas a medida que el protocolo madura

- **Integración de Seguridad de Microsoft**: Aprovecha el ecosistema de seguridad integral de Microsoft (Prompt Shields, Azure Content Safety, GitHub Advanced Security, Entra ID) para una protección mejorada del despliegue de MCP

## Recursos Integrales

### **Documentación Oficial de Seguridad de MCP**
- [MCP Specification (Current: 2025-11-25)](https://spec.modelcontextprotocol.io/specification/2025-11-25/)
- [MCP Security Best Practices](https://modelcontextprotocol.io/specification/2025-11-25/basic/security_best_practices)
- [MCP Authorization Specification](https://modelcontextprotocol.io/specification/2025-11-25/basic/authorization)
- [MCP GitHub Repository](https://github.com/modelcontextprotocol)

### **Recursos de Seguridad OWASP MCP**
- [OWASP MCP Azure Security Guide](https://microsoft.github.io/mcp-azure-security-guide/) - Guía completa OWASP MCP Top 10 con orientación de implementación en Azure
- [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) - Riesgos de seguridad oficiales de OWASP MCP
- [MCP Security Summit Workshop (Sherpa)](https://azure-samples.github.io/sherpa/) - Entrenamiento práctico de seguridad para MCP en Azure

### **Estándares de Seguridad y Mejores Prácticas**
- [OAuth 2.0 Security Best Practices (RFC 9700)](https://datatracker.ietf.org/doc/html/rfc9700)
- [OWASP Top 10 Web Application Security](https://owasp.org/www-project-top-ten/)
- [OWASP Top 10 for Large Language Models](https://genai.owasp.org/download/43299/?tmstv=1731900559)
- [Microsoft Digital Defense Report](https://aka.ms/mddr)

### **Investigación y Análisis de Seguridad de IA**
- [Prompt Injection in MCP (Simon Willison)](https://simonwillison.net/2025/Apr/9/mcp-prompt-injection/)
- [Tool Poisoning Attacks (Invariant Labs)](https://invariantlabs.ai/blog/mcp-security-notification-tool-poisoning-attacks)
- [MCP Security Research Briefing (Wiz Security)](https://www.wiz.io/blog/mcp-security-research-briefing#remote-servers-22)

### **Soluciones de Seguridad de Microsoft**
- [Microsoft Prompt Shields Documentation](https://learn.microsoft.com/azure/ai-services/content-safety/concepts/jailbreak-detection)
- [Azure Content Safety Service](https://learn.microsoft.com/azure/ai-services/content-safety/)
- [Microsoft Entra ID Security](https://learn.microsoft.com/entra/identity-platform/secure-least-privileged-access)
- [Azure Token Management Best Practices](https://learn.microsoft.com/entra/identity-platform/access-tokens)
- [GitHub Advanced Security](https://github.com/security/advanced-security)

### **Guías de Implementación y Tutoriales**
- [Azure API Management as MCP Authentication Gateway](https://techcommunity.microsoft.com/blog/integrationsonazureblog/azure-api-management-your-auth-gateway-for-mcp-servers/4402690)
- [Microsoft Entra ID Authentication with MCP Servers](https://den.dev/blog/mcp-server-auth-entra-id-session/)
- [Secure Token Storage and Encryption (Video)](https://youtu.be/uRdX37EcCwg?si=6fSChs1G4glwXRy2)

### **Seguridad de DevOps y Cadena de Suministro**
- [Azure DevOps Security](https://azure.microsoft.com/products/devops)
- [Azure Repos Security](https://azure.microsoft.com/products/devops/repos/)
- [Microsoft Supply Chain Security Journey](https://devblogs.microsoft.com/engineering-at-microsoft/the-journey-to-secure-the-software-supply-chain-at-microsoft/)

## **Documentación Adicional de Seguridad**

Para una orientación de seguridad completa, consulta estos documentos especializados en esta sección:

- **[MCP Security Best Practices 2025](./mcp-security-best-practices-2025.md)** - Mejores prácticas completas de seguridad para implementaciones de MCP
- **[Azure Content Safety Implementation](./azure-content-safety-implementation.md)** - Ejemplos prácticos de implementación para la integración de Azure Content Safety
- **[MCP Security Controls 2025](./mcp-security-controls-2025.md)** - Controles y técnicas de seguridad más recientes para despliegues de MCP
- **[MCP Best Practices Quick Reference](./mcp-best-practices.md)** - Guía de referencia rápida para las prácticas esenciales de seguridad de MCP

### **Entrenamiento Práctico de Seguridad**

- **[MCP Security Summit Workshop (Sherpa)](https://azure-samples.github.io/sherpa/)** - Taller práctico integral para asegurar servidores MCP en Azure con campamentos progresivos desde el Campamento Base hasta la Cumbre
- **[OWASP MCP Azure Security Guide](https://microsoft.github.io/mcp-azure-security-guide/)** - Arquitectura de referencia y guía de implementación para todos los riesgos del OWASP MCP Top 10

---

## Qué Sigue

Siguiente: [Capítulo 3: Primeros Pasos](../03-GettingStarted/README.md)
