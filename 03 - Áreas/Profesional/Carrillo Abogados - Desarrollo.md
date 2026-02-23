---
título: "Área: Desarrollo de Software — Carrillo Abogados"
tipo: área
empresa: "Carrillo Abogados"
rol: "Desarrollador / Arquitecto de Soluciones IA"
tags:
  - área
  - profesional
  - carrillo-abogados
  - desarrollo-software
  - legal-tech
última_actualización: 2026-02-22
---

# Desarrollo de Software — Carrillo Abogados

> **Área continua:** Rol profesional como desarrollador de la plataforma tecnológica de Carrillo Abogados.

---

## 🏗️ Stack Tecnológico

| Capa | Tecnología |
|------|-----------|
| Frontend | Next.js (React) |
| Backend | Spring Boot 3.3.13, Java 21 |
| Base de datos | PostgreSQL 16.2 |
| Mensajería | NATS |
| Infraestructura | Docker, Docker Compose |
| Build | Maven + Google Jib |
| Control de versiones | Git (branches: dev → staging → main) |

---

## 🚀 Proyectos Activos

```dataview
TABLE estado, prioridad, fecha_vencimiento AS "Vence"
FROM "02 - Proyectos/Carrillo Abogados"
WHERE estado = "activo"
SORT prioridad ASC
```

---

## 🔧 Herramientas de Trabajo

- [[04 - Recursos/Herramientas/Claude Code/Upgrade Agent Teams|Claude Code — Agent Teams & Configuración]]
- [[04 - Recursos/Herramientas/Obsidian/APIs y Keys|APIs y Keys de Integraciones]]

---

## 📋 Prácticas y Convenciones

- Git flow: `dev` → `staging` → `main`
- Microservicios: 8 servicios, puertos 8080-8800
- Build: `mvn clean package jib:buildTar` → `docker load`
- Claude Code workflow: `/session-start` → Plan Mode → Implementar → `/commit` → `/session-end`

---

## 💡 Conocimiento Técnico (→ Notas Permanentes)

- [[01 - Notas Permanentes/IA & LLMs/ZK020 - Arquitectura RAG|Arquitectura RAG]]
- [[01 - Notas Permanentes/Data Science/ZK010 - CRISP-DM|CRISP-DM aplicado al negocio]]
