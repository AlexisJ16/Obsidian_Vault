---
id: ZK010
título: "CRISP-DM: El Marco Iterativo para Proyectos de Ciencia de Datos"
fecha_creación: 2026-02-22
última_modificación: 2026-02-22
tags:
  - nota-permanente
  - crisp-dm
  - data-science
  - metodología
  - proyectos-datos
área: Data Science
fuentes:
  - "Análisis de Datos I - Universidad Icesi"
  - "Data Science Project Scoping Guide - Univ. Chicago"
relacionadas:
  - "[[ZK011 - Pregunta SMART en Data Science]]"
  - "[[ZK012 - Tipos de Analítica]]"
  - "[[ZK020 - Arquitectura RAG]]"
estado: consolidada
---

# CRISP-DM: El Marco Iterativo para Proyectos de Ciencia de Datos

## 💡 Idea central

> CRISP-DM (Cross Industry Standard Process for Data Mining) define 6 fases cíclicas para proyectos de datos. Su valor clave es que **no es lineal**: los hallazgos en fases tardías retroalimentan fases tempranas, haciendo del ciclo una espiral ascendente de comprensión.

---

## 📖 Las 6 Fases

```
        ┌─────────────────────────────────┐
        │                                 ▼
  [1] Business      [2] Data       [3] Data
  Understanding  → Understanding → Preparation
        ↑                                 │
        │                                 ▼
  [6] Deployment  ← [5] Evaluation ← [4] Modeling
        └─────────────────────────────────┘
```

| Fase | Pregunta central | Output |
|------|-----------------|--------|
| **1. Business Understanding** | ¿Qué problema de negocio resolvemos? | Pregunta SMART, criterios de éxito |
| **2. Data Understanding** | ¿Qué datos tenemos? ¿Son útiles? | EDA, reporte de calidad de datos |
| **3. Data Preparation** | ¿Cómo transformamos los datos? | Dataset limpio y listo para modelar |
| **4. Modeling** | ¿Qué modelo ajusta mejor? | Modelo entrenado + parámetros |
| **5. Evaluation** | ¿El modelo cumple los criterios? | Decisión de despliegue |
| **6. Deployment** | ¿Cómo lo integramos en producción? | Sistema funcionando en negocio |

---

## 📖 Fase 1 en profundidad: Business Understanding

Esta es la fase más crítica y más subestimada. Un proyecto bien formulado en fase 1 ahorra meses de trabajo.

**Preguntas clave a responder:**
1. ¿Cuál es el objetivo del negocio? (en lenguaje de negocio)
2. ¿Cómo traducimos eso a un problema analítico?
3. ¿Cuáles son los criterios de éxito medibles?
4. ¿Tenemos los datos necesarios?
5. ¿Qué recursos (tiempo, presupuesto, datos) están disponibles?

**Herramienta: Pregunta SMART** → ver [[ZK011 - Pregunta SMART en Data Science]]

---

## 📖 Aplicación al Proyecto Carrillo Abogados

El Taller 1 de Análisis de Datos I aplicó CRISP-DM Fases 1 y 2:
- **Problema de negocio:** 62% de consultas repetitivas, 3.2h diarias perdidas/abogado
- **Traducción analítica:** Clasificación de intenciones + generación RAG
- **Criterios de éxito:** Reducir tiempo de respuesta 75%, automatizar 70% de FAQs
- **Datos disponibles:** PostgreSQL (clientes, casos), PDFs legales, corpus jurídico colombiano

→ Ver proyecto completo: [[02 - Proyectos/MIAA - Universidad Icesi/Análisis de Datos I/Taller 1 - Formulación de Proyecto MIAA]]

---

## 🔗 Conexiones

- [[ZK011 - Pregunta SMART en Data Science]]
- [[ZK012 - Tipos de Analítica]]
- [[ZK020 - Arquitectura RAG]]
- [[02 - Proyectos/MIAA - Universidad Icesi/Análisis de Datos I/MOC - Análisis de Datos I]]

## 📌 Referencias

- Data Science Project Scoping Guide — Univ. Chicago Data Science for Social Good
- Sesión 1 CRISP-DM — José Armando Ordóñez, Análisis de Datos I, Icesi 2026
