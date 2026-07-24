# 🚀 SDAP: Spec-Driven Agentic Programming

> **El estándar metodológico que transforma el "prompteo" informal en ingeniería de software predecible, segura y auditable.**

![Diagrama](./images/infografia_sdap.svg)
*(Figura 1: Arquitectura de Doble Capa y Flujo de Ejecución Atómica SDAP)*

---

### 💡 ¿De qué trata esta metodología?

**Spec-Driven Agentic Programming (SDAP)** es un marco de trabajo diseñado para controlar y dirigir a los Agentes autónomos de IA durante el desarrollo de software.

En lugar de darle instrucciones ambiguas a la IA y dejar que modifique archivos libremente, SDAP establece una premisa fundamental:
> **"El humano diseña y restringe; la IA ejecuta e implementa."**

#### 🛡️ Pilares Principales:
* **Capa 0 (`.sdap/`):** El "genoma inmutable" del proyecto. Define las reglas de negocio, la arquitectura y los modelos de datos que la IA **nunca** puede violar.
* **Capa 1 (`docs/ai/`):** Un mapa de 15 archivos temáticos que le enseñan a la IA cómo navegar y entender la estructura del código existente.
* **Ejecución Atómica:** Cada tarea se delimita con diagramas de secuencia (`INTERFACE_FLOW.md`). La IA solo modifica lo necesario, reduciendo costos de tokens y eliminando la deriva de código.****


