---
fecha_creación: 2026-02-19
tags:
  - moc
  - dashboard
cssclasses:
  - dashboard
---

# 🏠 Dashboard — PKM Vault

> *"El conocimiento es poder. Organizado, es transformación."*

---

## 🗂️ Estructura del Vault

| Carpeta | Propósito |
|---------|-----------|
| [[00 - Inbox\|📥 Inbox]] | Captura rápida de ideas y notas en bruto |
| [[01 - Notas Permanentes\|💡 Notas Permanentes]] | Ideas procesadas y conocimiento destilado (Zettelkasten) |
| [[02 - Proyectos\|🚀 Proyectos]] | Proyectos activos con objetivos y tareas |
| [[03 - Áreas\|🌐 Áreas]] | Responsabilidades continuas (Académico, Profesional, Personal) |
| [[04 - Recursos\|📚 Recursos]] | Material de referencia (libros, artículos, cursos) |
| [[05 - Archivo\|🗄️ Archivo]] | Notas y proyectos completados o descartados |
| [[Diario\|📅 Diario]] | Notas diarias y semanales |

---

## 📊 Estadísticas del Vault

```dataview
TABLE length(rows) AS "Notas"
FROM ""
WHERE !contains(file.path, "Plantillas")
GROUP BY split(file.folder, "/")[0] AS Carpeta
SORT Carpeta ASC
```

---

## 📥 Inbox reciente

```dataview
LIST
FROM "00 - Inbox"
SORT file.mtime DESC
LIMIT 10
```

---

## 🚀 Proyectos activos

```dataview
TABLE estado, prioridad, fecha_vencimiento AS "Vence"
FROM "02 - Proyectos"
WHERE estado = "activo"
SORT prioridad ASC
```

---

## 📅 Notas recientes

```dataview
TABLE file.mtime AS "Modificado"
FROM ""
WHERE !contains(file.path, "Plantillas") AND file.name != "Dashboard"
SORT file.mtime DESC
LIMIT 15
```
