---
fecha: <% tp.date.now("YYYY-MM-DD") %>
día: <% tp.date.now("dddd", 0, "es") %>
tags:
  - diario
estado: activo
---

# 📅 <% tp.date.now("DD [de] MMMM [de] YYYY", 0, "es") %>

## 🌅 Intención del día
> ¿Cuál es mi intención principal para hoy?

## ✅ Tareas del día

- [ ] 
- [ ] 
- [ ] 

## 📝 Notas y reflexiones

## 🔗 Conexiones
> Ideas o notas relacionadas con lo de hoy.

## 🌙 Reflexión final
> ¿Qué aprendí hoy? ¿Qué puedo mejorar mañana?

---
**Ayer:** [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | **Mañana:** [[<% tp.date.now("YYYY-MM-DD", 1) %>]]
