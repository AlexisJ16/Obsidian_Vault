---
id: ZK020
título: "Arquitectura RAG: Generación Aumentada por Recuperación"
fecha_creación: 2026-02-22
última_modificación: 2026-02-22
tags:
  - nota-permanente
  - rag
  - llm
  - ia-generativa
  - arquitectura
  - vector-db
área: IA & LLMs
fuentes:
  - "Taller 1 - Análisis de Datos I - Icesi"
  - "Deployment of Machine Learning Models"
relacionadas:
  - "[[ZK021 - LLMs y Modelos de Lenguaje]]"
  - "[[ZK010 - CRISP-DM]]"
  - "[[ZK012 - Tipos de Analítica]]"
estado: consolidada
---

# Arquitectura RAG: Generación Aumentada por Recuperación

## 💡 Idea central

> RAG (Retrieval-Augmented Generation) resuelve el problema fundamental de los LLMs: las alucinaciones y el desconocimiento del dominio específico. En lugar de confiar solo en el conocimiento preentrenado, RAG **recupera documentos relevantes** de una base de datos vectorial y los inyecta como contexto al LLM antes de generar la respuesta.

---

## 📖 Componentes de una Arquitectura RAG

```
Usuario
   │ Query
   ▼
[1] Embedding del Query → Vector de alta dimensionalidad
   │
   ▼
[2] Vector DB (Búsqueda semántica)
   │   ┌─── Pinecone / Weaviate / pgvector
   │   └─── Corpus pre-indexado (PDF → chunks → embeddings)
   │ Top-K documentos relevantes
   ▼
[3] Prompt Engineering
   │   Context = Query + Documentos recuperados
   ▼
[4] LLM (GPT-4 / Claude / Llama)
   │ Respuesta fundamentada en los documentos
   ▼
Usuario ← Respuesta con citas verificables
```

---

## 📖 Por qué RAG sobre Fine-tuning

| Aspecto | RAG | Fine-tuning |
|---------|-----|-------------|
| **Actualización de conocimiento** | Instantánea (indexar nuevos docs) | Requiere re-entrenamiento |
| **Costo computacional** | Bajo | Alto |
| **Trazabilidad** | Alta (cita fuentes) | Baja (conocimiento difuso) |
| **Privacidad** | Documentos quedan locales | Datos en el entrenamiento |
| **Ideal para** | Dominios específicos con docs | Cambios de estilo/comportamiento |

**Conclusión:** Para el dominio legal colombiano, RAG es superior porque:
- El corpus jurídico se actualiza constantemente (nuevas sentencias)
- La trazabilidad legal es crítica (citar jurisprudencia exacta)
- Los datos de clientes son PII y no pueden entrenarse en modelos externos

---

## 📖 Pipeline de Ingesta (Data Engineering)

```
PDF / Documentos legales
   ↓ OCR (si son escaneados)
Texto crudo
   ↓ Chunking (dividir en fragmentos ~512 tokens)
Chunks
   ↓ Embedding model (OpenAI text-embedding-3, o local)
Vectores
   ↓ Indexar
Base de datos vectorial (pgvector o Pinecone)
```

---

## 📖 Consideraciones para el contexto legal colombiano

1. **Gobernanza:** Ley 1581/2012 (Habeas Data) — los datos PII se procesan localmente
2. **Chunking estratégico:** Artículos de ley = un chunk. Sentencias = por ratio/considerando
3. **Priorización del corpus:** 40% Derecho Civil, 20% Laboral → indexar primero estas áreas
4. **Idioma:** Embeddings en español nativo (multilingual-e5-large o similar)

---

## 🔗 Conexiones

- [[ZK021 - LLMs y Modelos de Lenguaje]]
- [[ZK010 - CRISP-DM]]
- [[ZK012 - Tipos de Analítica]]
- [[02 - Proyectos/Carrillo Abogados/Asistente Virtual Legal]]
