# CAPÍTULO IV: PROTOCOLOS DE INYECCIÓN, GUÍA OPERATIVA Y EVALUACIÓN

## 4.1. El Protocolo de Inyección de Contexto (*Context Injection Protocol*)

El éxito del estándar **Spec-Driven Agentic Programming (SDAP)** radica en transformar la interacción con el agente en un proceso determinista y acotado. Para evitar que el Modelo de Lenguaje (LLM) caiga en el fenómeno *Lost in the Middle* o sufra degradación por saturación de tokens, SDAP establece un protocolo estricto de empaquetado de payload para los prompts de ejecución mediante etiquetas del tipo XML.

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

## 4.2. Plantilla Estandarizada del Prompt de Ejecución (The SDAP Prompt)
A continuación se define la plantilla oficial de instrucción que el desarrollador (o la herramienta de orquestación) debe proveer al agente autónomo para la ejecución de una tarea de desarrollo:

### ROL Y MODO DE OPERACIÓN
Actúas como un Agente de Ejecución de Código estricto bajo la metodología Spec-Driven Agentic Programming (SDAP).
Tu único objetivo es implementar la tarea descrita sin desviarte de las fronteras arquitectónicas ni de las reglas de negocio provistas.

### REGLAS DE GOBERNANZA (INMUTABLES)
1. **Tech Fence:** No puedes agregar dependencias, librerías o paquetes externos no autorizados en `<governance_rules>`.
2. **Domain Logic:** Las reglas de validación y estados definidos en la máquina de estados de dominio son inviolables.
3. **Boundary Control:** Solo estás autorizado a modificar o crear archivos dentro del alcance definido en `<execution_boundary>`. Prohibido refactorizar o tocar código fuera de esta frontera.

### TAREA A EJECUTAR
- **Objetivo:** Implementar el paso [Nº] del Diagrama de Secuencia en `INTERFACEFLOW.md`.
- **Entrada esperada:** [Especificar DTO/Entidad de entrada].
- **Salida esperada:** [Especificar DTO/Respuesta esperada].

### INSTRUCCIÓN DE COMPORTAMIENTO
Analiza el flujo en `<execution_boundary>`, verifica las barreras de contención en `<guardrails>` y genera únicamente el código fuente necesario, acompañado de sus correspondientes pruebas unitarias bajo las convenciones del proyecto.

## 4.3. Casos de Uso Prácticos y Flujos de Trabajo (Workflows)
SDAP no solo rige la creación de código nuevo, sino que proporciona flujos de trabajo estandarizados para las operaciones habituales del ciclo de vida del software.

```mermaid
graph TD
    A[Requisito / Bug / Refactor] --> B{Tipo de Tarea}
    
    B -->|Nueva Feature| C[1. Co-Diseño: Actualizar .sdap/ & INTERFACE_FLOW.md]
    B -->|Corrección de Bug| D[2. Localización: Verificar si violó .sdap/ o código]
    B -->|Refactorización| E[3. Aislamiento: Congelar contratos en .sdap/DATA_MINDMAP.md]
    
    C --> F[Ejecución Atómica con Prompt SDAP]
    D --> F
    E --> F
    
    F --> G[Verificación de Guardrails & Tests]
    G --> H[Commit / PR Aprobado]

```
### 4.3.1. Caso de Uso A: Implementación de una Nueva Funcionalidad (*New Feature*)
* **Fase Inception Dialéctica:** El humano y la IA conversacional actualizan `.sdap/DOMAIN_LOGIC.md` si hay nuevas reglas y crean el `INTERFACEFLOW.md` del nuevo módulo.
* **Empaquetado Atómico:** Se inyecta la Capa 0, los guardrails (`docs/ai/14-ai-rules.md`) y el `INTERFACEFLOW.md` local.
* **Ejecución y Sincronización:** El agente genera el código y actualiza `docs/ai/` si hubo cambios en la infraestructura.

### 4.3.2. Caso de Uso B: Resolución de Incidentes (*Bug Fixing*)
* **Diagnóstico:** Se determina si el bug es por falla local o por un caso de borde no previsto en el dominio.
* **Ajuste de Especificación:** Si el bug reveló un caso de borde (*edge case*) no contemplado, primero se actualiza la especificación en `.sdap/DOMAIN_LOGIC.md` o el Diagrama de Secuencia local.
* **Ejecución Restringida:** Se inyecta la especificación corregida y el fragmento de código afectado.
* 

### 4.3.3. Caso de Uso C: Refactorización Controlada
1. **Congelamiento de Contratos:** Se valida que `.sdap/DATA_MINDMAP.md` (interfaces y DTOs) permanezca inmutable.
2. **Inyección de Reglas de Código:** Se enfatiza el archivo `docs/ai/04-coding-guidelines.md` en el payload.
3. **Ejecución:** El agente refactoriza la estructura interna del módulo sin alterar las firmas de las interfaces públicas expuestas en la Capa 0.

---

## 4.4. Barreras de Contención y Prevención de Deriva (*Guardrails*)

Para asegurar que los agentes autónomos operen con alta fidelidad, la Capa 1 define el archivo `docs/ai/14-ai-rules.md`. Este archivo actúa como una lista explícita de directivas relativas a la conducta del modelo:

### 4.4.1. Ejemplos de Guardrails (`docs/ai/14-ai-rules.md`)
* **Prohibición de Suposiciones Lógicas:** "Si un requisito o contrato de datos es ambiguo, detén la ejecución y solicita aclaración. No asumas campos opcionales ni inventes valores por defecto."
* **Prohibición de Modificaciones Masivas:** "Prohibido modificar archivos de configuración raíz (`package.json`, `tsconfig.json`, `Dockerfile`) a menos que el prompt lo ordene explícitamente."
* **Cero Código Muerto / TODOs:** "No dejes comentarios `// TODO:` ni bloques de código comentados."

### 4.4.2. El Rol del Agente Auditor (*Red-Teaming Pattern*)
Para garantizar el cumplimiento de la gobernanza, SDAP introduce un patrón de verificación de doble agente:
* **Agente Ejecutor:** Recibe el prompt SDAP y genera el código/PR.
* **Agente Auditor de Gobernanza:** Analiza el `git diff` resultante frente a `.sdap/ARCH_SKELETON.md` y `14-ai-rules.md`. Emite un reporte de aprobación (*PASS/FAIL*) identificando si el Agente Ejecutor cometió violaciones arquitectónicas o introdujo código fuera de la frontera permitida.

---

## 4.5. Conclusiones del Estándar SDAP

Para medir la efectividad de SDAP frente a enfoques empíricos o ad-hoc, el caso de estudio evalúa cuatro métricas cuantitativas clave:

* **Context Retention Rate (CRR):** Porcentaje de reglas de negocio en `.sdap/DOMAIN_LOGIC.md` respetadas sin alucinaciones durante la primera iteración.
* **Token Efficiency Index (TEI):** Relación entre tokens consumidos y líneas de código útil producidas ($Tokens / Lineas$). SDAP busca reducir esta tasa al evitar la inyección de repositorios completos.
* **Architecture Compliance Score (ACS):** Grado de cumplimiento de la valla tecnológica y ausencia de modificaciones no autorizadas fuera del `INTERFACEFLOW.md`.
* **Iterative Roundtrips to Success (IRS):** Número de intentos o correcciones necesarias por parte del desarrollador para que la solución pase todas las pruebas y revisiones de código.

### Conclusión Final

El estándar **Spec-Driven Agentic Programming (SDAP)** transforma el paradigma del desarrollo asistido por IA, transitando desde un modelo artesanal basado en prompts informales hacia una disciplina de ingeniería rigurosa, predecible y evolutiva. Al desvincular el descubrimiento dialéctico del problema (Capa 0) de la ejecución atómica del código (Capa 1), SDAP garantiza que la tecnología sirva a la preservación del conocimiento y a la calidad sostenida de la arquitectura del software.
