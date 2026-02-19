# 🧠 Obsidian Vault — PKM Personal

Repositorio de sincronización digital del Vault de Obsidian, orientado a la gestión del conocimiento personal (PKM), académico y profesional.

---

## 📁 Estructura del Vault

```
Obsidian_Vault/
├── 00 - Inbox/              # Captura rápida (bandeja de entrada)
├── 01 - Notas Permanentes/  # Conocimiento procesado (Zettelkasten)
├── 02 - Proyectos/          # Proyectos activos
├── 03 - Áreas/
│   ├── Académico/           # Estudios, materias, investigación
│   ├── Profesional/         # Trabajo, carrera, habilidades
│   └── Personal/            # Hábitos, salud, finanzas, reflexiones
├── 04 - Recursos/
│   ├── Libros/
│   ├── Artículos/
│   ├── Cursos/
│   └── Videos/
├── 05 - Archivo/            # Notas y proyectos completados
├── Diario/
│   ├── Diarios/             # Notas diarias
│   └── Semanales/           # Revisiones semanales
├── Plantillas/              # Plantillas reutilizables
├── Adjuntos/                # Imágenes y archivos multimedia
└── Dashboard.md             # Vista principal del vault
```

---

## 🔌 Plugins recomendados (Community Plugins)

| Plugin | Función |
|--------|---------|
| [Dataview](https://github.com/blacksmithgu/obsidian-dataview) | Consultas dinámicas sobre las notas |
| [Templater](https://github.com/SilentVoid13/Templater) | Plantillas avanzadas con variables y JavaScript |
| [Obsidian Git](https://github.com/denolehov/obsidian-git) | Sincronización automática con este repositorio |
| [Calendar](https://github.com/liamcain/obsidian-calendar-plugin) | Visualización de notas diarias en calendario |
| [Periodic Notes](https://github.com/liamcain/obsidian-periodic-notes) | Notas diarias, semanales y mensuales |
| [Tasks](https://github.com/obsidian-tasks-group/obsidian-tasks) | Gestión avanzada de tareas |
| [Recent Files](https://github.com/tgrosinger/recent-files-obsidian) | Acceso rápido a archivos recientes |

---

## 🗂️ Metodología

Este vault combina dos metodologías PKM líderes:

- **PARA** (Projects · Areas · Resources · Archive) — para organizar la información por accionabilidad.
- **Zettelkasten** — para construir una red de conocimiento permanente y atómico en `01 - Notas Permanentes`.

---

## ⚙️ Configuración de Obsidian Git

1. Instala el plugin **Obsidian Git** desde la tienda de plugins de la comunidad.
2. En los ajustes del plugin, configura:
   - **Vault backup interval**: `10` minutos (o el valor que prefieras).
   - **Auto pull interval**: `10` minutos.
   - **Commit message**: `vault backup: {{date}}`.
3. El archivo `.gitignore` ya está configurado para excluir `workspace.json` y la caché local.

---

## 🚀 Inicio rápido

1. Clona este repositorio en tu equipo:
   ```bash
   git clone https://github.com/AlexisJ16/Obsidian_Vault.git
   ```
2. Abre Obsidian → **Abrir carpeta como vault** → selecciona la carpeta clonada.
3. Instala los plugins listados arriba desde *Ajustes → Plugins de la comunidad*.
4. Abre `Dashboard.md` como punto de entrada principal.

---

## 📄 Licencia

Uso personal. Todos los derechos reservados © AlexisJ16.
