---
tags:
  - entrega-final
  - taller-1
  - proyecto-miaa
  - crisp-dm
  - legal-tech
estado: completado
fecha_entrega: 2026-02-20
autor: "Alexis Jaramillo Martinez"
docente: "José Armando Ordóñez Córdoba"
curso: "Análisis de Datos I (2026-I) - Universidad Icesi"
---

## Proyecto: Asistente Virtual Legal con Arquitectura RAG (Carrillo Abogados)

> [!ABSTRACT] Resumen Ejecutivo
> El presente documento enmarca la fase inicial de **Comprensión del Negocio y de los Datos** (fases 1 y 2 de la metodología CRISP-DM) para el desarrollo de un Asistente Virtual Legal. El objetivo es resolver cuellos de botella operativos en atención al cliente y optimizar el tiempo de investigación jurídica mediante técnicas de IA Generativa y Analítica Predictiva.

---

## 🏗️ PARTE 1: Informe Narrativo (Fundamentación Analítica)

### 1. Justificación del tipo de IA / Analítica:

El Asistente Virtual Legal de Carrillo Abogados no es un chatbot tradicional basado en reglas, sino una solución integral que recorre el espectro completo de la madurez analítica enseñado en el curso:

* **Analítica Descriptiva (¿Qué pasó?):** Se utilizará para monitorear el histórico del CRM (schema `clients`), perfilando patrones de consulta, tiempos de espera actuales y cuellos de botella en la atención.
* **Analítica Predictiva (¿Qué pasará?):** Mediante modelos de Procesamiento de Lenguaje Natural (NLP), el sistema realizará clasificación multiclase para predecir la intención del usuario (ej. consulta, seguimiento, urgencia) y alimentará el *lead scoring* para estimar la probabilidad de conversión antes de asignar un abogado humano.
* **IA Generativa / Prescriptiva (¿Cómo resolvemos el problema?):** El núcleo del asistente emplea un Modelo de Lenguaje Grande (LLM) orquestado con una arquitectura **RAG (Retrieval-Augmented Generation)**. Consultará bases de datos vectoriales alimentadas con jurisprudencia colombiana y el historial del bufete para redactar respuestas precisas, generar borradores de documentos y sugerir cursos de acción legales de forma autónoma.

Se selecciona esta arquitectura avanzada porque el dominio legal exige una comprensión semántica profunda, manejo de ambigüedades y la generación de texto fundamentado en hechos reales (mitigando alucinaciones), superando ampliamente las capacidades de los árboles de decisión convencionales.

### 2. Descripción de los Datos y Disponibilidad (2 pts)

El modelo de datos se fundamenta en un ecosistema híbrido de fuentes internas y externas, abarcando datos estructurados y no estructurados:

* **Fuentes Internas Estructuradas (Disponibilidad: Alta):** El bufete opera actualmente con PostgreSQL 16.2. Extraeremos datos del schema `clients` (perfiles y lead scoring de 30-100 pts), schema `cases` (tipología y timeline procesal) y schema `notifications` (interacciones previas).
* **Fuentes Internas No Estructuradas (Disponibilidad: Media-Alta):** Documentos legales, contratos y memoriales en formato PDF (schema `documents`) que requerirán pipelines de Ingeniería de Datos (OCR, chunking y vectorización).
* **Fuentes Externas (Disponibilidad: Pública):** Corpus jurídico colombiano (Constitución Política, Ley 1564/2012, Ley 599/2000) y sentencias de la Relatoría de la Corte Constitucional y Consejo de Estado.

**Gobernanza y Ética:** En cumplimiento estricto del *secreto profesional* y la **Ley 1581 de 2012 (Habeas Data)**, se implementará un pipeline de anonimización de entidades nombradas (PII) antes de cualquier proceso de *embedding* o *fine-tuning*. Los datos sensibles operarán en inferencia local, garantizando que ninguna información identificable sea expuesta a APIs de terceros.

---

## 📊 PARTE 2: Formulario de Excel (Matriz de Proyecto)

| Campo Solicitado                                  | Respuesta para el Formulario                                                                                                                                                                                                                                                                                                                                                                                           |
| :------------------------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**                                        | Alexis Jaramillo Martinez                                                                                                                                                                                                                                                                                                                                                                                              |
| **Sector de la empresa**                          | Servicios Legales / LegalTech                                                                                                                                                                                                                                                                                                                                                                                          |
| **Tamaño de la empresa**                          | 50 empleados                                                                                                                                                                                                                                                                                                                                                                                                           |
| **Descripción del problema e impacto (métricas)** | **Problema:** El 62% de las consultas de clientes son repetitivas (FAQs), consumiendo 3.2 horas diarias por abogado. El tiempo de primera respuesta es de 4.8 hrs (laboral) y >18 hrs (no hábil), generando una tasa de abandono de leads del 35%. <br>**Impacto Financiero:** Pérdida de ~480 horas facturables anuales, equivalentes a un costo de oportunidad de $72M COP anuales (15% de la capacidad productiva). |
| **Tipo de analítica**                             | **IA Generativa y Predictiva:** Generación de contenido legal y respuestas (LLM+RAG) y clasificación predictiva de intenciones y calificación de leads (NLP).                                                                                                                                                                                                                                                          |
| **Caso similar (Estado del Arte)**                | **Harvey AI** (plataforma generativa respaldada por OpenAI para bufetes anglosajones) y **CoCounsel** (asistente legal de Thomson Reuters). Ninguna opera nativamente sobre el corpus judicial colombiano (oportunidad de innovación).                                                                                                                                                                                 |
| **Tipo de problema de IA**                        | Procesamiento de Lenguaje Natural (NLP), Generación de Texto (RAG), Búsqueda Semántica Vectorial y Clasificación Multiclase.                                                                                                                                                                                                                                                                                           |
| **Datos necesarios y disponibilidad**             | **Disponibles:** BBDD PostgreSQL (tablas de clientes, casos), PDFs legales internos, Corpus Jurídico Público de Colombia. <br>**Por recopilar:** Historiales de chats de WhatsApp Business.                                                                                                                                                                                                                            |
| **Impacto en el negocio (métricas)**              | 1) Reducir el tiempo de primera respuesta en un **75%** (de 4.8 hrs a <1.2 hrs). 2) Automatizar el **70%** de las consultas repetitivas. 3) Disminuir la tasa de abandono de leads del **35% al 15%**.                                                                                                                                                                                                                 |
| **Pregunta SMART**                                | *(Ver desglose en la siguiente sección)*                                                                                                                                                                                                                                                                                                                                                                               |

### 🎯 Desglose de la Pregunta SMART
> **¿Cómo puede un asistente virtual basado en IA generativa (RAG) integrado al CRM de Carrillo Abogados, reducir en un 75% el tiempo de primera respuesta a leads y automatizar el 70% de las consultas frecuentes, liberando 400 horas facturables anuales en un plazo de 6 meses desde su despliegue?**

* **[S] Específica:** Implementar un asistente virtual con arquitectura RAG para atención al cliente y apoyo jurídico.
* **[M] Medible:** Reducción del 75% en tiempo de respuesta, 70% de automatización de FAQs y 400 horas facturables recuperadas.
* **[A] Alcanzable:** Se cuenta con la infraestructura base (Next.js, PostgreSQL) y los datos estructurados necesarios.
* **[R] Relevante:** Ataca el dolor principal del bufete (costo de oportunidad en horas no facturables y pérdida de leads).
* **[T] Temporal:** Plazo de 6 meses a partir del inicio de la fase de despliegue.

---

## 🛠️ PARTE 3: Análisis Exploratorio de Datos (EDA) - Análisis Univariado

Para validar la viabilidad del proyecto y establecer la línea base (*baseline*) métrica antes de la implementación del Agente IA, se realizó un Análisis Exploratorio de Datos utilizando **Python (Pandas, Seaborn, Matplotlib)** sobre una muestra representativa y anonimizada de 500 interacciones históricas (leads).

### 3.1 Importancia de las Columnas Analizadas

1. **`response_time_minutes` (Numérica Continua):** Tiempo desde la creación del lead hasta la respuesta. **Relación con el objetivo:** Es la métrica KPI principal (a reducir en un 75%).
2. **`lead_score` (Numérica Continua):** Puntaje del cliente prospecto (30-100). **Relación con el objetivo:** Permite al IA derivar automáticamente los casos de alto valor (hot leads) a abogados humanos.
3. **`consultation_category` (Categórica Nominal):** Área jurídica. **Relación con el objetivo:** Define qué corpus legal documental (ej. Código Civil vs. Penal) debe priorizarse en la base de datos vectorial (Vector DB) del modelo RAG.
4. **`message_length` (Numérica Discreta):** Cantidad de caracteres del primer contacto. **Relación con el objetivo:** Vital para configurar los hiperparámetros del LLM (max_tokens, context window).
5. **`conversion_flag` (Categórica Binaria 0/1):** Indica cierre exitoso del caso. **Relación con el objetivo:** Variable objetivo (Target) para futuros modelos de clasificación predictiva.

### 3.2 Visualizaciones y Hallazgos Relevantes (Python)

![[Taller 1 - Formulación de Proyecto MIAA (Asistente Virtual Legal).png]]
![[1-Taller 1 - Formulación de Proyecto MIAA (Asistente Virtual Legal).png]]

**Interpretación y Hallazgos:**
* **Tiempo de Respuesta (Asimetría Positiva):** El histograma revela una asimetría pronunciada hacia la derecha (*right-skewed*). Aunque la media se sitúa cerca de los 250 minutos (~4 horas), existe una "cola larga" de casos atípicos (*outliers*) que esperan más de 10 horas. Estos representan las consultas nocturnas o de fin de semana, validando la necesidad de una atención IA 24/7.
* **Lead Score (Distribución y Outliers):** El *boxplot* muestra una distribución normal truncada con una mediana cercana a 55 puntos. La ausencia de *outliers* significativos por debajo de 30 indica que el filtro actual de captación funciona, pero el grueso de los leads está en una zona "tibia" (WARM), ideal para que un IA haga *nurturing* automático.
* **Categorías (Desbalance de Clases):** El análisis de frecuencias (*Bar chart*) demuestra que el Derecho Civil acapara el 40% del volumen, seguido del Laboral (20%). El modelo RAG deberá enfocar su primer entrenamiento de indexación semántica en la jurisdicción civil.
* **Longitud del Mensaje (Kurtosis):** La distribución log-normal muestra que la mayoría de los clientes envían mensajes cortos (menos de 100 caracteres), lo que sugiere que la IA necesitará habilidades de *prompting* iterativo para hacer preguntas aclaratorias al usuario antes de emitir un concepto legal.

---

## 📌 PARTE 4: Conclusiones del Análisis y Viabilidad del Negocio

1. **Justificación Cuantitativa del Proyecto:** El análisis univariado confirma el "dolor" principal del negocio. La dispersión en la métrica `response_time_minutes` evidencia cuellos de botella severos fuera del horario laboral. La implementación de un LLM mitigará inmediatamente esta curva, "aplanando" la distribución estadística hacia la izquierda (tiempos de respuesta casi inmediatos).
2. **Priorización del Desarrollo Técnico:** Dado que el 60% de los datos se concentran en Derecho Civil y Laboral, la fase de Ingeniería de Datos (ingesta, chunking y generación de embeddings en la base vectorial) iniciará exclusivamente con la normatividad de estas dos ramas, aplicando un enfoque de producto mínimo viable (MVP).
3. **Calidad de Datos y Siguientes Pasos:** La base de datos actual posee una estructura robusta y limpia para las métricas operativas. El siguiente paso en la metodología CRISP-DM (Preparación de Datos) requerirá el diseño de un *pipeline* de procesamiento de lenguaje natural (NLP) para limpiar y anonimizar el texto crudo contenido en los mensajes iniciales y PDFs, preparándolos para la inferencia del modelo RAG.



---

## 🤖 Declaración de Uso de IA Generativa (Nivel 4)
*En cumplimiento con las directrices de la Universidad Icesi sobre Inteligencia Artificial:*
Para la formulación de este documento y el refinamiento de la pregunta SMART, se utilizó asistencia de IA Generativa (GitHub Copilot y modelos conversacionales subyacentes). La IA operó en un rol de ideación y estructuración (framework CRISP-DM), alimentada estrictamente con el contexto técnico del repositorio de software propietario del autor. Todas las decisiones métricas, consideraciones éticas (Habeas Data) y la adaptación al marco teórico del curso fueron curadas, revisadas y validadas críticamente por el autor humano.