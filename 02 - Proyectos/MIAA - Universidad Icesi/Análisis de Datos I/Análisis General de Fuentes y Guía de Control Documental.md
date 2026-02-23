
## Análisis General de Fuentes y Guía de Control Documental

---

## 1. Análisis Detallado de la Base de Datos Actual

La documentación subida actualmente al cuaderno pertenece al curso de **Análisis de Datos I (Periodo 2026-I)** de la Universidad Icesi, impartido por el docente José Armando Ordoñez Cordoba. La información se puede agrupar en cuatro pilares fundamentales del ciclo de vida analítico:

### A. Estructura Administrativa y Logística del Curso

- **Fuentes vinculadas:** `0. Inicio y Presentación.md`, `0. Syllabus - Análisis de Datos - 1_2026_1.pdf`.
- **Análisis general:** El curso está diseñado en torno al marco CRISP-DM, complementado con fundamentos de Ingeniería de Datos (ingestión, calidad y arquitecturas modernas). Comprende 2 créditos académicos y 24 horas de intensidad. La metodología exige lectura previa, laboratorios en Jupyter Notebooks, y un proyecto final transversal que vale el 60% de la calificación.
- **Directriz de Inteligencia Artificial:** La institución promueve un uso "Nivel 4: IAG Completa", lo que significa que la IA generativa puede usarse estratégicamente, pero exige un informe técnico y creativo de 800 palabras para explicar y transparentar las decisiones éticas y técnicas tomadas.

### B. Planteamiento y Comprensión del Negocio (Scoping y CRISP-DM)

- **Fuentes vinculadas:** `1. Sesión 1 – Comprensión del negocio.md`, `2. Data Science Project Scoping Guide.md`, `4. Slides - Pregunta SMART.pdf`, `9. IBM – CRISP-DM 1.0 Step-by-step Data Mining Guide.pdf`.
- **Análisis general:** Todo proyecto debe comenzar comprendiendo los objetivos del negocio antes de tocar los datos. El paso inicial primordial es transformar problemas difusos en objetivos analíticos estructurados mediante la creación de **Preguntas SMART** (Específicas, Medibles, Alcanzables, Relevantes y enmarcadas en Tiempo). Asimismo, el "Scoping" (delimitación) exige identificar las fuentes de información internas/externas, las acciones derivadas del modelo y los riesgos éticos o de privacidad.

### C. Análisis Exploratorio y Fundamentos de Ingeniería de Datos

- **Fuentes vinculadas:** `1. Análisis Exploratorio de Datos.pdf`, `6. Sesión 3 - Fundamentos de Ingeniería de Datos.md`, `7. DICCIONARIO DE VARIABLES...pdf`, `Ejercicio - Dataset ICFES.md`.
- **Análisis general:** Para aplicar el modelado, es obligatoria la fase de Análisis Exploratorio de Datos (EDA), orientada a limpiar ruido, evaluar valores faltantes, identificar anomalías y analizar distribuciones (estadística descriptiva univariada y multivariada).
- A nivel de **Ingeniería**, se destaca el uso de archivos _Parquet_ por su eficiencia y la integración de arquitecturas como _Data Lake_, _Data Warehouse_ y _Lakehouse_ (combinación de los dos mundos) utilizando Microsoft Fabric y SQL. Se incluye un caso aplicado mediante el análisis de la Prueba Saber TyT, que exige revisar variables demográficas e institucionales guiándose de forma estricta por su diccionario de datos.

### D. Analítica, Modelado e Inteligencia Artificial

- **Fuentes vinculadas:** `2. Panorama actual de la IA y los Datos.pdf`, `3. Flujo de datos e IA - Parte I.pdf`, `4. Deployment of Machine learning Models.md`, `5. Sesión 2 - Tipos de Analítica y Modelado.md`.
- **Análisis general:** Los datos sirven para cuatro niveles de analítica: Descriptiva (qué pasó), Diagnóstica (por qué pasó), Predictiva (qué sucederá usando _Machine Learning_) y Prescriptiva (usar los modelos para probar estrategias y optimizar).
- Se enseñan las subdivisiones del aprendizaje automático: supervisado (regresión y clasificación con datos etiquetados), no supervisado (_clustering_ para agrupación de clientes) y por refuerzo.
- Además, se contemplan despliegues prácticos de estos modelos usando Flask y Docker en entornos Cloud (Azure), con un fuerte énfasis en que los modelos no sean "cajas negras", priorizando la interpretabilidad para el negocio.

---

## 2. Guía General para el Control y Gestión Documental

Para mantener el entorno analítico organizado, escalable y libre de ambigüedades, debes implementar las siguientes reglas para todo documento o _dataset_ que subas a la aplicación:

### I. Nomenclatura Estandarizada de Archivos

Mantén el prefijo numérico evolutivo que ya se evidencia en la base de datos.

- **0. o 00_:** Documentación administrativa, Syllabus, cronogramas y encuadres de la materia.
- **1., 2., 3., etc.:** Sesiones de clase o unidades de aprendizaje cronológicas.
- **GUI_ / REF_:** Guías de referencia metodológicas u oficiales (ej. Manual de IBM CRISP-DM).
- **DAT_ / EJER_:** Ejercicios prácticos, laboratorios y sus respectivas bases de datos.

### II. Uso de Metadatos Obligatorios (Frontmatter)

Todo documento de texto (Markdown) subido a la aplicación debe contar con un encabezado en la parte superior que facilite la indexación semántica:

- **tags:** Palabras clave (`#crisp-dm`, `#ingeniería-de-datos`, `#eda`, etc.).
- **estado:** Indica si la lectura está `pendiente`, `en-progreso` o `completada`.
- **relación:** Si el documento es un laboratorio, debe incluir un enlace escrito hacia la guía teórica a la que pertenece.

### III. Gestión Estricta de Datos y Diccionarios

- **Regla de Co-ocurrencia:** Jamás se debe subir un _dataset_ crudo sin su correspondiente diccionario de datos. Todo campo de una tabla debe tener descrito su tipo de variable (Categórica, Numérica) y los valores válidos esperados.
- Diferencia en los reportes cuándo hablas de la fuente primaria original ("Datos iniciales") y cuándo hablas de la data limpia ("Dataset reformateado/construido").

### IV. División del Código vs. Teoría

- Dado que el stack tecnológico del curso incluye Python y repositorios en GitHub, utiliza **esta aplicación** estrictamente para la gestión del conocimiento teórico, el análisis de negocio (las preguntas SMART), informes de EDA y control de metodología.
- Mantén el código fuente (Jupyter Notebooks) alojado y versionado nativamente en GitHub, referenciándolos aquí únicamente a través de "Accesos Rápidos" o hipervínculos.

### V. Auditoría de Artefactos CRISP-DM

Por cada proyecto en desarrollo (como el proyecto final), asegúrate de tener una "Nota Maestra" que funcione como _Project Plan_. Esta debe ir marcando la finalización de los reportes obligatorios de la metodología:

1. Reporte de Contexto y Pregunta de Negocio.
2. Reporte de Calidad y Exploración de Datos.
3. Reporte de Limpieza y Construcción.
4. Reporte de Evaluación, Despliegue y Mantenimiento.


