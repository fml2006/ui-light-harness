# Evaluación y decisiones · 25/09/2026

## Veredicto

La especialización tiene sentido: una app funcional, objetivo visual concreto y cambios
locales reducen la incertidumbre. El ahorro viene de reducir contexto y decisiones,
reutilizar el código y cerrar antes; no de elegir siempre el modelo más barato.
No hace falta un orquestador adicional para este recorrido secuencial.

## Compatibilidad de clientes

Las reglas visuales son comunes. Codex entra por AGENTS.md y Claude Code por CLAUDE.md,
que importa esa entrada breve. El contrato largo se lee solo al activar UI Light.
El soporte de instrucciones no aporta automáticamente navegador, autenticación ni
herramientas al otro cliente. No hay delegación entre proveedores en este modo.
La V0.1.1 añade esa entrada y guía; no implica pruebas reales en ambos clientes.

## Modelo y esfuerzo

La [documentación oficial de Luna](https://developers.openai.com/api/docs/models/gpt-6-luna)
confirma entrada de imágenes y tareas focalizadas. La [guía de selección](https://developers.openai.com/api/docs/guides/model-selection)
orienta Luna medium a cambios coordinados sobre trabajo existente. Por eso es el
candidato inicial **para Codex**. Claude Code conserva el modelo/esfuerzo elegidos
por el equipo; no se impone un modelo equivalente sin evaluar el piloto. Esto no demuestra precisión visual suficiente sobre nuestros proyectos.
Low podría evaluarse después para ajustes mínimos inequívocos; no se cambia esfuerzo
automáticamente en mitad del piloto. Sol/Opus quedan para una escalación justificada,
también si la dificultad es CSS/visual. Astra/Fable no son el siguiente paso por defecto.

## Cambios respecto del handoff

1. **BEFORE obligatorio:** permite separar diferencias de layout de datos, fuentes o estado.
2. **Capturas comparables:** ancho y alto CSS, DPR, tema y condiciones de render. El nombre
   desktop-1440 no alcanza para reproducir una pantalla por sí solo.
3. **Dos pasadas definidas:** dos lotes, cada uno con toda su validación. No dos screenshots,
   no dos intentos por viewport. Se conserva el contador tras interrupciones.
4. **Prioridad explícita:** el target guía estilo; un pedido explícito que lo modifica y
   las restricciones de funcionalidad/accesibilidad no quedan subordinados a la imagen.
5. **DONE con evidencia:** autoverificación visual y funcional dirigida. Sin render o con
   criterio necesario no comprobado, no se inventa un PASS.
6. **Contexto mínimo:** mapa del proyecto una vez, búsqueda local, hasta ocho grupos de
   diferencias, docs auxiliares bajo demanda. Un único reporte vivo por tarea.
7. **Memoria con fuentes:** Candidate no se vuelve Confirmed por afirmación del agente.
8. **Límites honestos:** las instrucciones no garantizan tope de créditos ni dos pasadas.

## Integración con el kit robusto

Dos modos distintos, con entrega humana común:

- **Independiente:** dev → agente del cliente elegido → checks + comparación visual → resultado al dev.
  La nueva propuesta autoriza este modo sin QA de otro proveedor; no se presenta como
  si ofreciera la misma garantía que v3. No hay push ni merge automático.
- **Integrado (diseño, no implementado):** orquestador fuerte clasifica una vez → worker
  UI Light → evidencia → QA cruzado del kit → aprobación del dev para entrega.
  La comparación visual del worker es autoverificación; no consume una ronda de QA
  externo ni lo sustituye. El PASS externo debe incluir los AC visuales pertinentes.

Para integrar de verdad faltan tres cambios específicos: registrar Luna como worker UI
en una ruta explícita, transportar capturas/manifiesto hacia un revisor con acceso a
imágenes y vincular esa evidencia al candidato, y hacer persistente el límite de dos
lotes bajo el ledger. No basta con editar el nombre del modelo: v3 hoy valida citas
de código y checks, no este protocolo visual multimodal. No implementamos esos cambios
ni debilitamos el gate actual sin resultados del piloto.

En v3 las correcciones tras un FAIL deben respetar el total visual consumido: agotar
dos lotes entrega NEEDS_REVIEW/escalación, no reinicia UI Light dentro de otro QA.
No agregar un QA cosmético de Opus a cada microedición por defecto: esa sobrecarga
eliminaría parte del ahorro que buscamos en el modo independiente.

## Qué no se puede prometer aún

La configuración local es un default sujeto a confianza y precedencias del cliente,
no selección infalible. Las capturas requieren herramientas de cada proyecto. La
autoverificación puede pasar por alto fallos. Un diff pequeño puede afectar un componente
compartido. Un precio menor por token no garantiza menor costo por cambio aceptado.
Estas incertidumbres se comprueban con un piloto acotado, no sumando agentes.
