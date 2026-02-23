---
fecha_creación: 2026-02-19
última_actualización: 2026-02-22
tags:
  - moc
  - dashboard
cssclasses:
  - dashboard
---

# PKM Vault — Centro de Comando

> *"El conocimiento capturado sin conexión es solo almacenamiento. Conectado, es inteligencia."*

---

## ⚡ Acciones Rápidas

| Acción | Destino |
|--------|---------|
| 📥 Nueva idea rápida | [[00 - Inbox/\|→ Inbox]] |
| 💡 Crear nota permanente | Plantilla: [[Plantillas/Nota Permanente\|Nota Permanente]] |
| 📅 Nota de hoy | Plantilla: [[Plantillas/Nota Diaria\|Nota Diaria]] |
| 🔍 Explorar Zettelkasten | [[01 - Notas Permanentes/MOC - Índice General\|Índice General]] |

---

## 🗂️ Estructura PARA

| Nivel | Carpeta | Propósito | Horizonte |
|-------|---------|-----------|----------|
| 📥 | [[00 - Inbox\|Inbox]] | Captura rápida — fleeting notes | < 48 horas |
| 💡 | [[01 - Notas Permanentes\|Notas Permanentes]] | Zettelkasten: ideas atómicas y conectadas | Permanente |
| 🚀 | [[02 - Proyectos\|Proyectos]] | Metas con fecha límite | Semanas/meses |
| 🌐 | [[03 - Áreas\|Áreas]] | Responsabilidades continuas | Sin fecha fin |
| 📚 | [[04 - Recursos\|Recursos]] | Material de referencia por tema | Sin vencimiento |
| 🗄️ | [[05 - Archivo\|Archivo]] | Proyectos completados e inactivos | Histórico |

---

## 🚀 Proyectos Activos

```dataview
TABLE estado, prioridad, fecha_vencimiento AS "Vence"
FROM "02 - Proyectos"
WHERE estado = "activo"
SORT prioridad ASC
```

---

## 🌐 Áreas en Curso

```dataview
TABLE tipo, última_actualización AS "Actualizado"
FROM "03 - Áreas"
SORT file.mtime DESC
```

---

## 💡 Zettelkasten — Notas Permanentes Recientes

```dataview
TABLE área, estado, fecha_creación AS "Creada"
FROM "01 - Notas Permanentes"
WHERE file.name != "MOC - Índice General"
SORT fecha_creación DESC
LIMIT 10
```

---

## 📥 Inbox — Pendiente de Procesar

```dataview
LIST
FROM "00 - Inbox"
SORT file.mtime DESC
LIMIT 10
```

---

## 📅 Notas Diarias Recientes

```dataview
LIST
FROM "Diario/Diarios"
SORT file.name DESC
LIMIT 7
```

---

## 📊 Estado del Vault

```dataview
TABLE length(rows) AS "Notas"
FROM ""
WHERE !contains(file.path, "Plantillas") AND !contains(file.path, ".obsidian")
GROUP BY split(file.folder, "/")[0] AS Carpeta
SORT Carpeta ASC
```

---

## 🗺️ Navegación Rápida

### Proyectos MIAA
- [[02 - Proyectos/MIAA - Universidad Icesi/Análisis de Datos I/MOC - Análisis de Datos I|Análisis de Datos I (2026-I)]]
- [[02 - Proyectos/MIAA - Universidad Icesi/Aprendizaje Automático|Aprendizaje Automático (2026-I)]]

### Proyectos Profesionales
- [[02 - Proyectos/Carrillo Abogados/Asistente Virtual Legal|Asistente Virtual Legal — Carrillo Abogados]]

### Áreas
- [[03 - Áreas/Académico/MIAA - Universidad Icesi|MIAA — Universidad Icesi]]
- [[03 - Áreas/Profesional/Carrillo Abogados - Desarrollo|Desarrollo — Carrillo Abogados]]

### Zettelkasten — MOC
- [[01 - Notas Permanentes/MOC - Índice General|Índice General]]
- [[01 - Notas Permanentes/Data Science/ZK010 - CRISP-DM|CRISP-DM]]
- [[01 - Notas Permanentes/IA & LLMs/ZK020 - Arquitectura RAG|Arquitectura RAG]]
