---
semana: <% tp.date.now("gggg-[W]ww") %>
fecha_inicio: <% tp.date.now("YYYY-MM-DD", 1 - tp.date.now("d")) %>
fecha_fin: <% tp.date.now("YYYY-MM-DD", 7 - tp.date.now("d")) %>
tags:
  - semanal
---

# 📆 Semana <% tp.date.now("ww [de] YYYY") %>

## 🎯 Objetivos de la semana

- [ ] 
- [ ] 
- [ ] 

## 📋 Revisión de proyectos activos

```dataview
TABLE WITHOUT ID file.link AS "Proyecto", estado, prioridad, fecha_vencimiento AS "Vence"
FROM "02 - Proyectos"
WHERE estado = "activo"
SORT prioridad ASC
```

## 📅 Días de la semana

| Día | Destacado |
|-----|-----------|
| Lunes | |
| Martes | |
| Miércoles | |
| Jueves | |
| Viernes | |
| Sábado | |
| Domingo | |

## 📝 Notas importantes de la semana

## 🔄 Revisión semanal

### ¿Qué fue bien?

### ¿Qué puede mejorar?

### ¿Qué voy a hacer diferente la próxima semana?
