---
título: "MOC — <% tp.file.title %>"
tipo: moc
área:
tags:
  - moc
última_actualización: <% tp.date.now("YYYY-MM-DD") %>
---

# <% tp.file.title %> — Mapa de Contenido

> Descripción del área/tema que organiza este MOC.

---

## 📋 Contenido principal

| Nota | Descripción |
|------|-------------|
| [[]] | |

---

## 💡 Notas Permanentes relacionadas

```dataview
TABLE área, estado, fecha_creación AS "Creada"
FROM "01 - Notas Permanentes"
WHERE contains(tags, "ETIQUETA_AQUÍ")
SORT fecha_creación DESC
```

---

## 🔗 Conexiones con otras áreas

- [[]]

---

## 📈 Próximas notas a crear

- [ ] ZKxxx —
