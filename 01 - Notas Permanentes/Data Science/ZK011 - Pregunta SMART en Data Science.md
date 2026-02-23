---
id: ZK011
título: "La Pregunta SMART como Traductor entre Negocio y Analítica"
fecha_creación: 2026-02-22
última_modificación: 2026-02-22
tags:
  - nota-permanente
  - smart
  - formulación-problemas
  - data-science
  - crisp-dm
área: Data Science
fuentes:
  - "Análisis de Datos I - Universidad Icesi"
relacionadas:
  - "[[ZK010 - CRISP-DM]]"
  - "[[ZK012 - Tipos de Analítica]]"
estado: consolidada
---

# La Pregunta SMART como Traductor entre Negocio y Analítica

## 💡 Idea central

> Una pregunta SMART traduce el dolor empresarial vago ("queremos mejorar la atención al cliente") en un problema analítico concreto y verificable. Es el artefacto más importante de la Fase 1 de CRISP-DM porque define el éxito del proyecto completo.

---

## 📖 Marco SMART

| Letra | Criterio | Pregunta de verificación |
|-------|----------|--------------------------|
| **S** — Specific | ¿Es suficientemente específica para saber exactamente qué construir? | ¿Alguien externo la entendería sin contexto adicional? |
| **M** — Measurable | ¿Tiene métricas concretas de éxito? | ¿Puedes poner un número? |
| **A** — Achievable | ¿Es técnicamente y operativamente posible con los recursos disponibles? | ¿Tienes los datos y el tiempo? |
| **R** — Relevant | ¿Ataca el problema de negocio real? | ¿Si lo logras, el negocio mejora en lo que importa? |
| **T** — Time-bound | ¿Tiene un plazo definido? | ¿Cuándo se considera exitoso? |

---

## 📖 Antipatrones comunes

1. **Pregunta vaga:** "¿Cómo mejorar la satisfacción del cliente?" — No medible, no específica
2. **Pregunta técnica sin contexto de negocio:** "¿Qué modelo de clasificación tiene mejor F1-score?" — No conecta con el valor del negocio
3. **Pregunta sin datos disponibles:** Plantear algo para lo que no se tienen datos aún
4. **Desconexión métrica:** La métrica de éxito del modelo no es la misma que la del negocio

---

## 📖 Ejemplo: Carrillo Abogados

**Pregunta SMART formulada:**
> *¿Cómo puede un asistente virtual basado en IA generativa (RAG) integrado al CRM de Carrillo Abogados, **reducir en un 75% el tiempo de primera respuesta** a leads y **automatizar el 70% de las consultas frecuentes**, liberando 400 horas facturables anuales en un plazo de **6 meses** desde su despliegue?*

**Verificación:**
- ✅ S: Define exactamente qué (RAG + CRM), qué hace (reducir respuesta, automatizar)
- ✅ M: 75%, 70%, 400h — métricas concretas
- ✅ A: Infraestructura base existe (PostgreSQL, Next.js)
- ✅ R: Ataca el costo de oportunidad de $72M COP/año
- ✅ T: 6 meses desde despliegue

---

## 🔗 Conexiones

- [[ZK010 - CRISP-DM]]
- [[ZK012 - Tipos de Analítica]]
- [[ZK020 - Arquitectura RAG]]
