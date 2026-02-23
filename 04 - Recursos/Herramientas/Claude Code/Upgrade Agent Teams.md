2. Análisis Exhaustivo: Qué Puede Hacer Claude Code con la Configuración Actual

  A. Agent Teams (Equipos de Agentes)

  Qué es: Múltiples instancias de Claude Code trabajando en paralelo, coordinadas por un "team lead", con task list compartido y mensajería directa entre agentes.

  Cómo funciona:
  - Un session (tú hablando conmigo) actúa como team lead
  - Se crean teammates — cada uno es una instancia independiente de Claude con su propio context window
  - Los teammates se comunican entre sí via mensajes directos (no solo reportan al lead)
  - Hay un task list compartido donde los agentes reclaman y completan tareas
  - Usa file locking para evitar race conditions cuando dos agentes intentan reclamar la misma tarea

  Modos de display:
  - in-process (el nuestro): todos corren en la misma terminal, Shift+Down para ciclar entre teammates
  - tmux/iTerm2: split panes, cada agente en su propio panel (no disponible en Windows)

  B. Extended Thinking (Pensamiento Extendido)

  Qué es: alwaysThinkingEnabled: true activa razonamiento profundo en cada respuesta.

  Cómo funciona: Claude tiene un "scratchpad" interno donde razona paso a paso antes de responder. Esto mejora significativamente:
  - Análisis de bugs complejos
  - Decisiones arquitectónicas
  - Refactoring multi-archivo
  - Resolución de conflictos de merge

  Trade-off: Más lento pero más preciso. Con effortLevel: high, Claude invierte máximo esfuerzo en cada respuesta.

  C. Subagents Personalizados

  Qué es: Agentes especializados definidos en .claude/agents/ que Claude puede delegar tareas específicas.

  Configuración disponible:
  - tools: Qué herramientas puede usar (Read, Write, Edit, Bash, Grep, Glob)
  - model: Qué modelo usar (opus, sonnet, haiku)
  - permissionMode: Nivel de permisos (default, acceptEdits, dontAsk, plan)
  - memory: Memoria persistente entre sesiones (user, project, local)
  - hooks: Lifecycle hooks propios del subagent
  - skills: Skills precargados en el contexto
  - isolation: worktree: Ejecutar en un git worktree aislado
  - background: true: Correr en segundo plano

  D. Skills (Habilidades Personalizadas)

  Qué es: Archivos SKILL.md que extienden el conocimiento de Claude con instrucciones, workflows, y slash commands reutilizables.

  Tipos:
  - Reference content: Conocimiento que Claude aplica automáticamente (convenciones, patrones)
  - Task content: Workflows paso a paso invocados con /nombre (deploy, commit, review)

  Features avanzados:
  - $ARGUMENTS para pasar parámetros
  - !command para inyectar contexto dinámico (output de comandos shell)
  - context: fork para ejecutar en un subagent aislado
  - disable-model-invocation: true para workflows manuales únicamente

  E. Hooks (Automatización Determinista)

  Qué es: Comandos shell que se ejecutan automáticamente en puntos específicos del ciclo de vida de Claude.

  Eventos disponibles:

  ┌────────────────────┬───────────────────────────────────┬────────────────────────────┐
  │       Evento       │         Cuándo se dispara         │         Uso típico         │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ SessionStart       │ Al iniciar/reanudar sesión        │ Cargar contexto            │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ PreToolUse         │ Antes de ejecutar una herramienta │ Validar/bloquear comandos  │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ PostToolUse        │ Después de usar herramienta       │ Auto-formatear, lint       │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ Stop               │ Cuando Claude termina             │ Verificar tareas completas │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ Notification       │ Cuando Claude necesita atención   │ Desktop notifications      │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ SubagentStart/Stop │ Al crear/terminar subagents       │ Setup/cleanup              │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ ConfigChange       │ Cambios en configuración          │ Auditoría                  │
  ├────────────────────┼───────────────────────────────────┼────────────────────────────┤
  │ PreCompact         │ Antes de compactación             │ Preservar contexto crítico │
  └────────────────────┴───────────────────────────────────┴────────────────────────────┘

  Tipos de hooks:
  - command: Script shell determinista
  - prompt: LLM de una sola vuelta (juicio rápido)
  - agent: Subagent que puede leer archivos y verificar condiciones

  F. Permisos Pre-aprobados

  Lo que configuramos permite:
  - Git: status, diff, log, branch, add, stash (lectura + staging)
  - Maven: todas las operaciones de build
  - Docker: ps, images, logs, inspect, compose ps/logs
  - WSL: kubectl get/describe/logs, helm list/status
  - Bloqueados: git push --force, docker system prune, rm -rf /

  ---
  3. Plan Estratégico: Cómo Aprovechar Esto para Carrillo Abogados

  3.1 Subagents Especializados para el Proyecto

  Recomiendo crear estos subagents en .claude/agents/:

  a) security-reviewer.md — Revisor de seguridad legal
  - Tools: Read, Grep, Glob (solo lectura)
  - Model: opus (máxima capacidad para seguridad)
  - Foco: OWASP top 10, datos sensibles de clientes, validación de inputs
  - Justificación: Sistema legal maneja datos PII de clientes — la seguridad es crítica

  b) microservice-tester.md — Tester de microservicios
  - Tools: Read, Bash, Grep, Glob
  - Model: sonnet (rápido para tests)
  - Foco: Ejecutar tests unitarios e integración por servicio
  - Justificación: Con 8 servicios, los tests se pueden paralelizar

  c) api-contract-validator.md — Validador de contratos API
  - Tools: Read, Grep, Glob
  - Model: haiku (rápido, solo lectura)
  - Foco: Verificar que cambios en DTOs no rompen contratos entre servicios
  - Justificación: En microservicios, los contratos API son el punto más frágil

  d) spring-boot-expert.md — Experto en Spring Boot 3.3
  - Tools: Read, Edit, Write, Bash, Grep, Glob
  - Model: opus
  - Skills: spring-conventions, jib-build
  - Justificación: Conocimiento profundo del stack específico

  3.2 Skills Específicos para el Proyecto

  a) .claude/skills/spring-conventions/SKILL.md — Convenciones Spring Boot
  Patrones de: error handling, DTOs, entity mapping, security config,
  schema-per-service, NATS event publishing con @Nullable, etc.

  b) .claude/skills/deploy-local/SKILL.md — Deploy local completo
  disable-model-invocation: true (manual con /deploy-local)
  Steps: mvn clean package jib:buildTar → docker load → docker compose up

  c) .claude/skills/lead-api/SKILL.md — API de Leads (n8n integration)
  Convenciones del Lead Scoring, webhook URLs, callback endpoints,
  categorías HOT/WARM/COLD, integración con n8n Cloud

  3.3 Agent Teams: Casos de Uso Concretos

  Caso 1: Implementar un nuevo feature que afecta múltiples servicios
  Crea un equipo de 4 agentes para implementar [feature]:
  - Agent 1: Implementar el endpoint en case-service
  - Agent 2: Implementar el DTO y evento NATS
  - Agent 3: Implementar el frontend en Next.js
  - Agent 4: Escribir tests de integración
  Requiere aprobación de plan antes de implementar.

  Caso 2: Code review paralelo de un PR grande
  Crea un equipo de 3 revisores para el PR:
  - Revisor 1: Seguridad (datos PII, OWASP)
  - Revisor 2: Performance (queries, N+1, memory leaks)
  - Revisor 3: Cobertura de tests y edge cases

  Caso 3: Debugging con hipótesis competidoras
  Crea 3 agentes para investigar [bug]:
  - Agente 1: Hipótesis de problema en gateway routing
  - Agente 2: Hipótesis de problema en serialización/deserialización
  - Agente 3: Hipótesis de problema en security config
  Que debatan y confronten sus teorías.

  3.4 Hooks Recomendados

  a) Notificación de escritorio (Windows):
  "Notification": [{
    "matcher": "",
    "hooks": [{
      "type": "command",
      "command": "powershell.exe -Command \"[System.Windows.Forms.MessageBox]::Show('Claude necesita atención', 'Claude Code')\""
    }]
  }]

  b) Re-inyectar contexto después de compactación:
  "SessionStart": [{
    "matcher": "compact",
    "hooks": [{
      "type": "command",
      "command": "echo 'RECORDATORIO: Stack=Spring Boot 3.3.13, Java 21, 8 microservicios. Build: mvn jib:buildTar. Git: dev→staging→main. Puertos: 8080-8800.'"
    }]
  }]

  3.5 Workflow Óptimo Diario

  1. /session-start              ← Skill existente: carga estado del proyecto
  2. Describir tarea del día
  3. Plan Mode (Ctrl+Shift+G)    ← Claude explora, planifica, tú apruebas
  4. Implementación               ← Con subagents para exploración pesada
  5. /stack-status                ← Verificar servicios healthy
  6. /commit                      ← Commit con atribución
  7. /session-end                 ← Guardar resumen al coordination hub

  3.6 Mejores Prácticas Críticas

  8. /clear entre tareas no relacionadas — El context window es el recurso más importante. No mezcles debugging de client-service con features de payment-service en la misma sesión.
  9. Subagents para investigación pesada — Cuando necesites explorar muchos archivos (ej: "cómo funciona la autenticación"), usa subagents. Así la exploración no contamina tu contexto
  principal.
  10. Verificación siempre — Incluye tests o criterios de verificación en cada prompt. "Implementa X y ejecuta los tests para verificar que funciona" es 10x mejor que solo "Implementa X".
  11. Agent Teams solo cuando hay paralelismo real — No uses teams para tareas secuenciales. El overhead de coordinación + tokens es significativo. Úsalos cuando los agentes realmente pueden
   trabajar independientemente en archivos diferentes.
  12. CLAUDE.md conciso — El actual tiene ~400 líneas. Recomiendo podar a ~200. Si Claude ya hace algo correctamente sin la instrucción, elimínala. Mover detalles específicos a Skills.
  13. Sesiones como branches — Usa claude --resume para retomar contexto. Nombra sesiones con /rename (ej: "oauth-migration", "lead-api-v2").

  ---
  Esa es la radiografía completa. Los features más impactantes para Carrillo Abogados en orden de prioridad son:

  14. Subagents personalizados (security-reviewer, api-contract-validator) — protección inmediata
  15. Skills del proyecto (spring-conventions, deploy-local) — consistencia en cada sesión
  16. Agent Teams para features multi-servicio — productividad x3-4 en tareas paralelas
  17. Hooks de notificación y compactación — calidad de vida diaria

  Si quieres, puedo implementar cualquiera de estos componentes ahora mismo.