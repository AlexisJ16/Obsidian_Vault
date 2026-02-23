---
id: ZK002
título: "Tipos de Notas en Zettelkasten y su Flujo de Procesamiento"
fecha_creación: 2026-02-22
última_modificación: 2026-02-22
tags:
  - nota-permanente
  - zettelkasten
  - pkm
  - flujo-notas
área: PKM
fuentes:
  - "Sönke Ahrens - How to Take Smart Notes"
relacionadas:
  - "[[ZK001 - PARA + Zettelkasten]]"
  - "[[ZK003 - Flujo de Procesamiento de Notas]]"
estado: consolidada
---

# Tipos de Notas en Zettelkasten y su Flujo de Procesamiento

## 💡 Idea central

> En Zettelkasten, cada nota tiene un propósito distinto. La clave está en el flujo: capturar rápido (Fleeting), extraer de fuentes (Literature) y consolidar en ideas propias (Permanent). No todas las notas son permanentes — la mayoría son insumos.

---

## 📖 Tipos de notas

### 1. Notas Volantes (Fleeting Notes)
- **Qué son:** Capturas instantáneas de pensamientos, ideas, observaciones
- **Formato:** Cualquier formato, incluso desordenado
- **Dónde:** `00 - Inbox/` o `Diario/Diarios/`
- **Ciclo de vida:** Máximo 48 horas antes de procesar o descartar
- **Ejemplo:** "El Derecho Civil representa 40% del volumen en Carrillo — priorizar en el índice vectorial"

### 2. Notas de Literatura (Literature Notes)
- **Qué son:** Ideas extraídas de una fuente específica, escritas en tus propias palabras
- **Formato:** Una idea por nota, referencia a la fuente, paginación
- **Dónde:** `04 - Recursos/` junto al material fuente
- **Regla:** Si no puedes explicarlo con tus palabras, no lo has entendido
- **Ejemplo:** Nota sobre el capítulo X de "Building a Second Brain"

### 3. Notas Permanentes (Permanent Notes / Zettels)
- **Qué son:** Ideas atómicas, autónomas, refinadas y conectadas
- **Formato:** `ZKxxx - Título descriptivo (afirmación)`, frontmatter completo
- **Dónde:** `01 - Notas Permanentes/` organizado por área conceptual
- **Criterios de calidad:**
  - [ ] Es atómica (una sola idea)
  - [ ] Es autónoma (se entiende sin contexto)
  - [ ] Está escrita en mis propias palabras
  - [ ] Tiene al menos 2 conexiones con otras notas
  - [ ] Tiene un título que es una afirmación, no un tema

### 4. MOC — Mapa de Contenido (Map of Content)
- **Qué son:** Notas de índice que agrupan y conectan notas permanentes por tema
- **Formato:** Lista de enlaces a notas, con descripción breve de cada una
- **Dónde:** `01 - Notas Permanentes/` o raíz de cada área
- **Propósito:** Puntos de entrada navegables al Zettelkasten
- **Ejemplo:** `MOC - Data Science`, `MOC - IA & LLMs`

---

## 📊 Flujo de Procesamiento

```
Lectura/Experiencia
      ↓
Fleeting Note (Inbox) ← captura rápida, 30 segundos
      ↓ (dentro de 48h)
¿Vale la pena procesar?
  ↓ NO → Archivar o Borrar
  ↓ SÍ
Literature Note (en tus palabras + fuente)
      ↓ (al revisitar)
¿Genera una idea propia?
  ↓ NO → Queda como Literature Note
  ↓ SÍ
Permanent Note (atómica, conectada, con ID ZKxxx)
      ↓
Conectar con notas existentes → Actualizar MOC
```

---

## 🔗 Conexiones

- [[ZK001 - PARA + Zettelkasten]]
- [[ZK003 - Flujo de Procesamiento de Notas]]
