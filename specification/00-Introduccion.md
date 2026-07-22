# Propuesta de Investigación: Spec-Driven Agentic Programming (SDAP)

## 1. Título Tentativo
**Desarrollo de un marco metodológico y estándares de gobernanza de contexto para la optimización del desarrollo de software asistido por Modelos de Lenguaje (LLMs) y Agentes Autónomos.**

---

## 2. Planteamiento del Problema
En la actualidad, la adopción de Inteligencia Artificial en el ciclo de vida del desarrollo de software (SDLC) se ha centrado en el uso empírico e intuitivo de chats conversacionales y agentes autónomos. Sin embargo, este enfoque ad-hoc carece de estandarización, lo que genera tres problemas críticos en la ingeniería de software moderna:

* **Degradación y Deriva de Contexto (*Context Drift*):** Los desarrolladores saturan la ventana de atención de los modelos inyectando repositorios completos o código irrelevante, lo que provoca respuestas truncadas, alucinaciones semánticas y un consumo ineficiente de tokens debido a limitaciones físicas del mecanismo de auto-atención (*Lost in the Middle*).
* **Ausencia de un Gobierno de Arquitectura:** Al delegar tareas a agentes autónomos sin límites de diseño estrictos, se introduce deuda técnica, código duplicado o redundante y violaciones sistemáticas a las reglas de negocio y patrones de arquitectura del proyecto.
* **Falta de Estandarización en el Contexto del Código:** La ausencia de una estructura clara que documente las convenciones, patrones de interfaz, reglas de negocio y mapeo de archivos provoca que la IA improvise soluciones o destruya la compatibilidad del sistema existente.

**Pregunta de investigación:** ¿Cómo puede un marco metodológico basado en especificaciones modulares en Markdown (Capa 0: Genoma Raíz) combinado con una estructura agnóstica de contexto vivo del sistema (Capa 1: `docs/ai/`) y un protocolo manual de selección de contexto reducir el tiempo de desarrollo, mitigar las alucinaciones de la IA y preservar la integridad arquitectónica del software?

---

## 3. Índice Propuesto para el Documento de Investigación

### Capítulo I: Introducción y Fundamentos
* **1.1.** Introducción al Desarrollo Asistido por IA (El espectro Chat vs. Agente).
* **1.2.** El problema del Contexto en los Transformadores (Ventanas de contexto, costo de tokens y el fenómeno *Lost in the Middle*).
* **1.3.** Justificación del estándar SDAP (La arquitectura de doble capa: Gobernanza Raíz y Contexto de Código).

### Capítulo II: El Marco Metodológico SDAP (La Teoría)
* **2.1.** Fase de Co-Diseño Conversacional (*Human-AI Inception*).
* **2.2.** La Arquitectura Fractal de Documentación Raíz (Genoma del proyecto: `ARCH_SKELETON`, `DOMAIN_LOGIC`, `DATA_MINDMAP`, `INTERFACE_FLOW`).
* **2.3.** Modelado Visual para IAs: El uso de Mermaid como lenguaje de abstracción lógica (Diagramas C4, Máquinas de Estado, ERD y Secuencia).
* **2.4.** Principio de Ejecución Atómica Atada a Diagramas.

### Capítulo III: Estructuración del Contexto Vivo y Gobernanza del Repositorio (La Práctica)
* **3.1.** El Esqueleto Tecnológico de Contexto: Estructura agnóstica de 15 archivos en `docs/ai/`.
* **3.2.** Protocolo de Carga Manual de Contexto por Tarea (Matriz de selección de archivos según el tipo de intervención en el código).
* **3.3.** El Sistema de Barreras (*Guardrails*) y Definición de Reglas Inviolables para Agentes de IA (`14-ai-rules.md`).

### Capítulo IV: Pruebas, Resultados y Conclusiones
* **4.1.** Caso de estudio (Desarrollo/mantenimiento de un módulo aplicando el estándar SDAP vs. Desarrollo empírico tradicional).
* **4.2.** Métricas de evaluación (Precisión de la respuesta de la IA, número de iteraciones requeridas, consumo de tokens y preservación de arquitectura).
* **4.3.** Conclusiones y líneas de trabajo futuro.
