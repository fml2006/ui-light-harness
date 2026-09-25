# Cómo usar UI Light

Para el equipo de frontend: actualizar pantallas de una app que ya funciona a partir
de screenshots. Un agente hace el cambio, lo comprueba y termina en hasta dos pasadas.

**El sitio actual aporta la marca; el screenshot aporta el cambio.** Se reutilizan
logos, tipografías, colores, tokens y componentes del proyecto. No hay que diseñar
la app de nuevo ni preparar un design system.

## 1. Preparar cada proyecto una sola vez

Este repositorio contiene las reglas, no la aplicación donde vas a trabajar.
Descargalo o clonalo. Luego abrí **tu app existente** en Codex **o Claude Code** y pedí lo siguiente,
reemplazando la ruta entre corchetes por la ubicación real del kit:

```text
Integrá UI Light desde [ruta local del kit] en esta app.
Copiá harness/ui sin pisar archivos existentes e integrá sus instrucciones
AGENTS.md, CLAUDE.md y exclusiones .gitignore con las nuestras.
Conservá una sola copia del procedimiento común en harness/ui.
Completá EXISTING-UI.md con los comandos y herramientas ya disponibles
para levantar esta app, capturar pantallas y comprobar el cambio.
Registrá las fuentes de branding que usa actualmente el sitio.
No instales dependencias ni modifiques la UI durante esta preparación.
Conservá el modelo y esfuerzo actuales de la herramienta que estoy usando.
```

Elegí la herramienta de trabajo; no necesitás ejecutar ambas:

| Herramienta | Entrada | Modelo |
|---|---|---|
| Codex | AGENTS.md | El paquete propone GPT-6 Luna medium mediante .codex/config.toml |
| Claude Code | CLAUDE.md, que importa AGENTS.md | El modelo/esfuerzo ya configurados por el equipo en Claude Code |

Solo para un entorno **Codex dedicado a UI Light**, podés agregar al pedido:
“Integrá las claves de .codex/config.toml del kit sin borrar otras configuraciones”.
No apliques ese default a un repo mixto gobernado por el orquestador completo.
Claude Code no usa esa configuración de Codex ni ejecuta Luna por leer estas reglas.
En Claude Code, revisá `/context` para comprobar que se cargaron las instrucciones.

El modelo elegido debe poder inspeccionar imágenes. Comprobá también el acceso al
navegador/capturas: las herramientas de una sesión no se heredan automáticamente en
la otra. Al cambiar de cliente, retomá el mismo UI-ID y contador; no vuelvas a cero
ni trabajes simultáneamente sobre la misma tarea desde ambos.

El responsable verifica el arranque, acceso a la pantalla, capturas y checks. El
agente puede completar el mapa desde el código; pregunta solo por información que
no pueda obtener, como acceso o estado específico. Nunca guardar contraseñas.

Antes de ejecutar un piloto con consumo, registrar autorización con alcance, intentos
y tope total. Reutilizar una autorización vigente sin pedirla en cada paso. Una cuenta
activa no la reemplaza; el kit no compra créditos ni impone un límite duro de gasto.

## 2. Pedir una actualización

Guardá la imagen en `harness/ui/references/targets/`. Abrí la app preparada en Codex o Claude Code,
no la carpeta de este kit. Ejemplo con un target aprobado de tu producto:

```text
Usá UI Light en /dashboard.
Target aprobado: harness/ui/references/targets/dashboard__desktop-1440__default__target.png
Viewport: 1440×900 CSS px, DPR 1, tema claro.
Actualizá la distribución, tamaños y espaciados para seguir el screenshot.
Conservá branding, datos, comportamiento y responsive actuales.
Reutilizá componentes y estilos. Validá con capturas, máximo dos pasadas.
```

Si el screenshot viene de otro sitio:

```text
Usá UI Light en /clientes.
Referencia: harness/ui/references/targets/clientes__desktop-1440__inspiracion.png
Es inspiración de layout: quiero esa distribución de tabla y filtros.
Adaptala a la marca actual de nuestro sitio. No copies su logo, fuentes ni paleta.
Mantené filtros, navegación, datos y responsive. Validá en hasta dos pasadas.
```

Si querés cambiar un atributo de marca, decilo expresamente y acotá el alcance,
por ejemplo: “Solo en esta card, usar el fondo del target; mantener la paleta global”.
Si tenés desktop y mobile, adjuntá ambos. Con solo desktop se conserva el mobile actual.

## 3. Qué vas a recibir

- Estado y pasadas usadas, archivos cambiados y capturas antes/después.
- Comprobaciones realizadas y cualquier diferencia pendiente.
- **DONE:** cumplió los criterios comprobados. El dev revisa el resultado.
- **NEEDS_REVIEW:** agotó dos pasadas; entrega lo logrado sin seguir gastando.
- **BLOCKED / ESCALATE:** falta un recurso o el pedido requiere otro alcance.

No abre subagentes ni cambia a un modelo caro automáticamente. No hace push ni
despliega como parte del ajuste visual. Las aprobaciones de entrega siguen siendo
las del proyecto. Un cambio de API, autenticación o lógica pasa al flujo principal.

## Qué probar primero

Una pantalla conocida y un cambio acotado: reorganizar cards, ajustar un formulario
o corregir espaciados. Usá un screenshot claro y una ruta que ya puedas abrir localmente.
La fidelidad y el ahorro deben medirse por modelo y herramienta en esa app; no están
garantizados. Compatibilidad de instrucciones no equivale a un piloto ya aprobado.

[Flujo visual](docs/ui-workflow.html) · [Plan de piloto](docs/PILOTO.md) ·
[Mantenimiento](docs/MANTENIMIENTO.md)
