# UI Light Harness · V1

**Un agente, una UI existente, hasta dos pasadas visuales.** Paquete de instrucciones
para usar desde **Codex o Claude Code**, con las mismas reglas visuales.
Codex incluye un default de piloto GPT-6 Luna medium; Claude Code conserva el modelo
y esfuerzo configurados por el equipo. No es una aplicación,
un motor de screenshots ni un sistema multiagente. No se ejecutaron modelos reales
para validarlo. **Empezá por [USO.md](USO.md)**: instalación y ejemplos para el equipo.
[Flujo visual](docs/ui-workflow.html) · [Evaluación crítica](docs/DECISIONES.md).

## Qué resuelve

Ajustes de layout, CSS, tipografía, colores, assets existentes, responsive y pequeños
cambios de markup. Ejemplos: igualar un dashboard aprobado, ajustar cards y formularios
o corregir spacing de una pantalla. Preserva comportamiento, datos y semántica.

**Conserva la marca del sitio actual:** logos, tipografías, colores y tokens existentes.
El screenshot define la actualización pedida; una referencia externa no autoriza un rebranding.

No cubre una app nueva, autenticación, pagos, APIs, estado complejo ni refactors amplios.
Una tarea visual también puede superar al modelo elegido: se escala con evidencia.

## Preparación una vez por proyecto

Un dev responsable integra el paquete en la raíz de una app existente:

1. Copiar `harness/ui/` y, opcionalmente, `docs/ui-workflow.html` con sus documentos
   enlazados. Integrar `AGENTS.md` y, para Claude Code, `CLAUDE.md`, sin reemplazar
   instrucciones existentes. La entrada de Claude importa la misma entrada breve
   mediante `@AGENTS.md`; no duplica el procedimiento.
2. Completar `harness/ui/EXISTING-UI.md`: cómo levantar la app, abrir la ruta, capturar
   screenshots y ejecutar checks con herramientas ya disponibles. No instalar un
   segundo framework de tests o navegador por defecto.
3. En **Codex**, para un proyecto/worktree **dedicado a UI Light**, integrar las dos claves de
   `.codex/config.toml`. No sobrescribir configuraciones existentes ni aplicar Luna
   al repo mixto donde el orquestador principal necesita Sol/Opus.
4. Integrar las exclusiones de `.gitignore` sin reemplazar las del proyecto. Targets,
   reportes y capturas se conservan localmente o en almacenamiento privado aprobado.
5. Antes del piloto real: disponer de autorización de consumo con alcance, intentos
   y tope total efectivo. Por defecto el consumo autorizado es cero. No comprar nada.

El archivo de configuración fija `model = "gpt-6-luna"` y
`model_reasoning_effort = "medium"`. Codex omite la configuración local de proyectos
no confiables; selecciones explícitas, sesiones ya abiertas y políticas administradas
pueden prevalecer. Comprobar una vez el modelo efectivo al abrir una tarea nueva.
No cambia el modelo de esta conversación ni la configuración global del equipo.
Fuente: [configuración de Codex](https://learn.chatgpt.com/docs/config-file/config-reference).

Claude Code usa `CLAUDE.md` para cargar las instrucciones comunes. Su modelo y esfuerzo
se gestionan en Claude Code: este paquete no impone Sonnet/Opus ni modifica permisos,
MCP o autenticación. Verificar la carga de instrucciones en `/context` y registrar el
modelo efectivo en la tarea. Si faltan herramientas para leer/capturar imágenes, BLOCKED.
Fuentes: [memoria e imports de Claude Code](https://code.claude.com/docs/en/memory) y
[configuración de modelos](https://code.claude.com/docs/en/model-config).

## Uso cotidiano

El dev pone los targets en `harness/ui/references/targets/`, abre el proyecto preparado
en Codex **o Claude Code** y pide:

```text
Usá UI Light. Actualizá /dashboard para que coincida con
harness/ui/references/targets/dashboard__desktop-1440__default__target.png.
El target corresponde a 1440×900 CSS px, DPR 1, tema claro y estado default.
Conservá branding, comportamiento y datos actuales. Preservá el responsive existente.
Validá visualmente y terminá en hasta dos pasadas.
```

La autorización de consumo puede estar ya registrada: reutilizarla dentro de su alcance,
sin pedirla otra vez. Si falta, el ejemplo no la reemplaza. El agente completa la tarea
y conserva el contador. No hace falta que el dev orqueste ni elija revisores.

Flujo: target + BEFORE → auditoría agrupada → patch → render/checks/comparación →
DONE, o una única corrección residual → DONE / NEEDS_REVIEW. No siempre usa dos pasadas.

## Archivos y lectura selectiva

| Archivo | Función |
|---|---|
| `USO.md` | Guía práctica para instalarlo y pedir cambios |
| `AGENTS.md` | Entrada breve compartida, activación y límites |
| `CLAUDE.md` | Entrada de Claude Code que importa AGENTS.md |
| `.codex/config.toml` | Default solo para Codex en proyecto UI dedicado |
| `harness/ui/UI-LIGHT.md` | Contrato de ejecución y cierre |
| `harness/ui/REFERENCE-POLICY.md` | Resolver fuentes, estados y conflictos |
| `harness/ui/EXISTING-UI.md` | Mapa operativo completado una vez |
| `harness/ui/UI-PATTERNS.md` | Memoria mínima con procedencia; empieza vacía |
| `harness/ui/BRAND-SOURCES.md` | Solo atributos de marca comprobados |
| `harness/ui/CHECKLIST.md` | Comprobación final con evidencia |
| `harness/ui/templates/UI-TASK.md` | Una tarea con entrada, contador y resultado |
| `harness/ui/references/` | Targets, ejemplos aprobados y marca |
| `docs/DECISIONES.md` | Criterio de modelo, límites e integración futura |
| `docs/MANTENIMIENTO.md` | Distribución, versiones y actualización sin perder memoria |
| `docs/PILOTO.md` | Cómo evaluar calidad, cierre y costo sin autoejecutar |
| `docs/ui-workflow.html` | Explicación para el equipo; no cargarla en cada tarea |

## Relación con Harness Kit v3

Esta es la distribución independiente para frontend. El kit completo conserva una copia
del módulo, pero **no está conectado a su runner ni a su instalador**. Las dos copias
no se sincronizan automáticamente: ver [mantenimiento](docs/MANTENIMIENTO.md).
No se agregó Luna a las rutas de implementación/QA generales. UI Light independiente
termina con autoverificación y entrega al dev; nunca autoriza un push.

Si la tarea pertenece a una spec gobernada por v3, no usar UI Light para saltar su ledger
o QA cruzado. La integración requiere incorporar el contrato visual y las capturas al
runner. Hasta hacerlo, conservar el flujo v3 para esas tareas. Ver [decisiones](docs/DECISIONES.md).

## Límite real de esta V1

Dos pasadas es una regla de instrucciones con registro manual, no un contador impuesto
por software. No hay medidor ni tope duro de tokens/créditos; tampoco ahorro o fidelidad
demostrados. Sin app, targets y entorno configurado no hay validación visual posible.
La pregunta del [piloto](docs/PILOTO.md) es si este flujo entrega cambios aceptables con
menos costo total y sin regresiones, incluyendo el tiempo de corrección del dev.
