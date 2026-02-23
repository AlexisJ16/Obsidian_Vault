---
id: ZK012
título: "Los 4 Tipos de Analítica: Espectro de Madurez en Ciencia de Datos"
fecha_creación: 2026-02-22
última_modificación: 2026-02-22
tags:
  - nota-permanente
  - analítica
  - data-science
  - madurez-analítica
área: Data Science
fuentes:
  - "Análisis de Datos I - Sesión 2 - Universidad Icesi"
relacionadas:
  - "[[ZK010 - CRISP-DM]]"
  - "[[ZK020 - Arquitectura RAG]]"
estado: consolidada
---

# Los 4 Tipos de Analítica: Espectro de Madurez en Ciencia de Datos

## 💡 Idea central

> Los 4 tipos de analítica forman un espectro ascendente de valor y complejidad. Cada nivel responde una pregunta diferente y requiere capacidades distintas. Un proyecto de IA maduro integra los 4 tipos.

---

## 📖 El Espectro

```
Valor  ▲                              IA Generativa/Prescriptiva
       │                          ¿Qué debería hacer? → Acción autónoma
       │                     ──────────────────────────────────────────
       │                 Analítica Predictiva
       │             ¿Qué pasará? → Clasificación, Regresión, Forecast
       │         ──────────────────────────────────────────────────────
       │     Analítica Diagnóstica
       │ ¿Por qué pasó? → Correlaciones, Análisis de causas raíz
       │ ────────────────────────────────────────────────────────────
       │ Analítica Descriptiva
       │ ¿Qué pasó? → Dashboards, KPIs, Reportes
       └──────────────────────────────────────────────► Complejidad
```

| Tipo | Pregunta | Técnicas | Ejemplo Carrillo |
|------|---------|----------|-----------------|
| **Descriptiva** | ¿Qué pasó? | Estadística, SQL, BI | KPIs del CRM: tiempo de respuesta promedio, leads por área |
| **Diagnóstica** | ¿Por qué? | Correlación, drill-down | ¿Por qué el 35% de leads abandonan? (tiempo de respuesta > 4h) |
| **Predictiva** | ¿Qué pasará? | ML, Clasificación, Regresión | Lead scoring: probabilidad de conversión antes de asignar abogado |
| **Prescriptiva/IA Gen.** | ¿Qué hacer? | LLM, RAG, Optimización | Respuesta automática generada + derivación a abogado si score > 70 |

---

## 📖 Aplicación en el Asistente Virtual Legal

El proyecto Carrillo Abogados integra los 4 tipos:
1. **Descriptiva:** Dashboard de métricas operativas (CRM PostgreSQL)
2. **Diagnóstica:** EDA sobre `response_time_minutes` y `consultation_category`
3. **Predictiva:** Clasificación de intención + lead scoring (NLP)
4. **IA Generativa:** LLM + RAG para respuestas autónomas 24/7

→ Ver: [[ZK020 - Arquitectura RAG]]

---

## 🔗 Conexiones

- [[ZK010 - CRISP-DM]]
- [[ZK011 - Pregunta SMART en Data Science]]
- [[ZK020 - Arquitectura RAG]]
