---
título: "Asistente Virtual Legal — Carrillo Abogados"
fecha_inicio: 2026-01-01
fecha_vencimiento: 2026-07-01
estado: activo
prioridad: alta
área: Profesional
tags:
  - proyecto
  - carrillo-abogados
  - legal-tech
  - rag
  - llm
  - ia-generativa
stack:
  - Next.js
  - Spring Boot 3.3
  - PostgreSQL 16
  - Docker
  - NATS
---

# Asistente Virtual Legal — Carrillo Abogados

## 🎯 Objetivo

> Implementar un asistente virtual con arquitectura RAG integrado al CRM de Carrillo Abogados que reduzca en un 75% el tiempo de primera respuesta y automatice el 70% de consultas repetitivas, liberando 400 horas facturables anuales en 6 meses.

---

## 📊 Métricas de Éxito

| Métrica | Baseline | Objetivo | Estado |
|---------|---------|---------|--------|
| Tiempo de primera respuesta | 4.8 hrs | < 1.2 hrs | 🔲 |
| Automatización de FAQs | 0% | 70% | 🔲 |
| Tasa de abandono de leads | 35% | 15% | 🔲 |
| Horas facturables recuperadas | 0 | 400/año | 🔲 |

---

## 🏗️ Arquitectura del Sistema

### Stack Técnico
- **Frontend:** Next.js (interfaz de chat + dashboard)
- **Backend:** 8 microservicios Spring Boot 3.3 (Java 21)
- **Base de datos:** PostgreSQL 16.2 (schemas: clients, cases, notifications, documents)
- **Mensajería:** NATS (eventos entre microservicios)
- **IA:** LLM + RAG + Base de datos vectorial
- **Infraestructura:** Docker + Docker Compose

### Flujo RAG
```
Consulta cliente → Embedding → pgvector → Top-K chunks → LLM → Respuesta
```

→ Ver concepto completo: [[01 - Notas Permanentes/IA & LLMs/ZK020 - Arquitectura RAG]]

---

## 📋 Fases del Proyecto

- [x] **Fase 1:** Comprensión del negocio y formulación (CRISP-DM 1-2)
- [ ] **Fase 2:** Preparación de datos — Pipeline NLP + anonimización PII
- [ ] **Fase 3:** Modelado — Fine-tuning embeddings + configuración RAG
- [ ] **Fase 4:** MVP — Chat funcional con corpus civil y laboral
- [ ] **Fase 5:** Integración CRM — Webhook, lead scoring automático
- [ ] **Fase 6:** Despliegue y evaluación de métricas

---

## 📂 Recursos y Análisis

- [[02 - Proyectos/MIAA - Universidad Icesi/Análisis de Datos I/Taller 1 - Formulación de Proyecto MIAA (Asistente Virtual Legal)|Taller 1 MIAA — Formulación formal del proyecto]]
- [[04 - Recursos/Herramientas/Claude Code/Upgrade Agent Teams|Estrategia de desarrollo con Claude Code Agent Teams]]

---

## 🔗 Notas Permanentes relacionadas

- [[01 - Notas Permanentes/IA & LLMs/ZK020 - Arquitectura RAG|Arquitectura RAG]]
- [[01 - Notas Permanentes/Data Science/ZK010 - CRISP-DM|CRISP-DM]]
- [[01 - Notas Permanentes/Data Science/ZK012 - Tipos de Analítica|Tipos de Analítica]]

---

## 📅 Historial

| Fecha | Actividad |
|-------|-----------|
| 2026-02-20 | Entrega Taller 1 — Formulación CRISP-DM + EDA |
| 2026-02-22 | Documentación del proyecto en vault PKM |
