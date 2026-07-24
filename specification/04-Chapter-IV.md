# CAPÍTULO IV: PROTOCOLOS DE INYECCIÓN, GUÍA OPERATIVA Y EJECUCIÓN PRÁCTICA

## 4.1. El Protocolo de Inyección de Contexto (*Context Injection Protocol*)

El éxito del estándar **Spec-Driven Agentic Programming (SDAP)** radica en transformar la interacción con el agente en un proceso determinista y acotado. Para evitar que el Modelo de Lenguaje de Gran Escala (LLM) caiga en el fenómeno *Lost in the Middle* o sufra degradación por saturación de tokens, SDAP establece un protocolo estricto de empaquetado de payload para los prompts de ejecución.

### 4.1.1. Estructura Estándar del Payload
Cada invocación orientada a tareas de código (*task execution*) debe componerse exactamente de cuatro bloques lógicos, delimitados por etiquetas tipo XML para maximizar la capacidad de parséo semántico de los transformadores:

# CAPÍTULO IV: PROTOCOLOS DE INYECCIÓN, GUÍA OPERATIVA Y EJECUCIÓN PRÁCTICA

## 4.1. El Protocolo de Inyección de Contexto (*Context Injection Protocol*)

El éxito del estándar **Spec-Driven Agentic Programming (SDAP)** radica en transformar la interacción con el agente en un proceso determinista y acotado. Para evitar que el Modelo de Lenguaje de Gran Escala (LLM) caiga en el fenómeno *Lost in the Middle* o sufra degradación por saturación de tokens, SDAP establece un protocolo estricto de empaquetado de payload para los prompts de ejecución.

### 4.1.1. Estructura Estándar del Payload
Cada invocación orientada a tareas de código (*task execution*) debe componerse exactamente de cuatro bloques lógicos, delimitados por etiquetas tipo XML para maximizar la capacidad de parséo semántico de los transformadores:

```xml
<sdap_context>
  <!-- BLOQUE 1: RESTRICCIONES INMUTABLES (CAPA 0) -->
  <governance_rules>
    [Contenido o extracto relevante de .sdap/ARCH_SKELETON.md]
    [Contenido o extracto relevante de .sdap/DOMAIN_LOGIC.md]
  </governance_rules>

  <!-- BLOQUE 2: BARRERAS DE CONTENCIÓN (CAPA 1) -->
  <guardrails>
    [Contenido de docs/ai/14-ai-rules.md]
    [Contenido de docs/ai/04-coding-guidelines.md]
  </guardrails>

  <!-- BLOQUE 3: DELIMITACIÓN LOCAL DE LA TAREA -->
  <execution_boundary>
    [Contenido del INTERFACE_FLOW.md del módulo específico]
  </execution_boundary>

  <!-- BLOQUE 4: INSTRUCCIÓN ATÓMICA DE EJECUCIÓN -->
  <task_instruction>
    [Descripción puntual del objetivo, haciendo referencia explícita al Diagrama de Secuencia]
  </task_instruction>
</sdap_context>xml
<sdap_context>
  <!-- BLOQUE 1: RESTRICCIONES INMUTABLES (CAPA 0) -->
  <governance_rules>
    [Contenido o extracto relevante de .sdap/ARCH_SKELETON.md]
    [Contenido o extracto relevante de .sdap/DOMAIN_LOGIC.md]
  </governance_rules>

  <!-- BLOQUE 2: BARRERAS DE CONTENCIÓN (CAPA 1) -->
  <guardrails>
    [Contenido de docs/ai/14-ai-rules.md]
    [Contenido de docs/ai/04-coding-guidelines.md]
  </guardrails>

  <!-- BLOQUE 3: DELIMITACIÓN LOCAL DE LA TAREA -->
  <execution_boundary>
    [Contenido del INTERFACE_FLOW.md del módulo específico]
  </execution_boundary>

  <!-- BLOQUE 4: INSTRUCCIÓN ATÓMICA DE EJECUCIÓN -->
  <task_instruction>
    [Descripción puntual del objetivo, haciendo referencia explícita al Diagrama de Secuencia]
  </task_instruction>
</sdap_context>
```
