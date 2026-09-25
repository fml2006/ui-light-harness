# UI Light · contrato V1

Un agente actualiza una UI funcional. La referencia define la actualización visual
dentro del alcance pedido; el sitio actual aporta su marca y el código existente
guía la implementación. Conservar logos, fuentes, paleta y tokens salvo cambio
explícito de marca. Una captura externa aporta composición, no una nueva identidad. No reconstruir la pantalla ni diseñar
un sistema nuevo. No iniciar subagentes, revisores, investigación web ni generación
de assets por defecto. Luna medium es el candidato inicial, no calidad garantizada.

## Entrada y preparación

- Recibir ruta de pantalla y targets. Reutilizar una tarea existente; si no existe,
  crear un único `harness/ui/tasks/UI-ID.md` desde `templates/UI-TASK.md`. No exigir
  que el dev rellene todo: inferir del mapa del proyecto y registrar lo comprobado.
- Leer `EXISTING-UI.md` y validar comandos, rutas y disponibilidad del navegador.
  Fijar viewport CSS ancho×alto, DPR, zoom, tema, datos, estado e interacciones clave.
  El nombre de una imagen orienta; sus píxeles no prueban el viewport ni el DPR.
- Confirmar autorización de consumo con alcance, intentos y tope total. Una cuenta
  activa no basta. Si se exige un límite duro que el entorno no puede imponer,
  reportar BLOCKED antes de ejecutar modelos/servicios. Nunca comprar ni recargar.
- Revisar cambios previos para preservarlos. Localizar componente y estilos con
  búsqueda dirigida, siguiendo solo imports y consumidores relevantes. No recorrer
  todo el repo. Registrar archivos previstos y el estado inicial del checkout.
- Identificar la marca en los tokens, estilos y assets del área afectada; registrar
  sus fuentes en `BRAND-SOURCES.md` si aún no existen. No auditar todo el sitio ni
  pedir un manual de marca si el código y la UI actual bastan. Registrar el tipo de
  referencia y los cambios de marca explícitamente autorizados; por defecto, ninguno.
- Capturar BEFORE antes de editar, con la app real y recursos cargados. Inspeccionar
  visualmente target y BEFORE; no deducir el resultado solo leyendo código.
  Sin acceso a las imágenes o a un render reproducible: BLOCKED, sin parche a ciegas.

## Auditoría y patch agrupado

Revisar una vez toda la pantalla objetivo: contenedor, geometría, alineación,
espaciado, tipografía, colores, bordes, radios, sombras, assets, controles, wrapping,
overflow y responsive. Escribir como máximo ocho grupos de diferencias accionables,
no una narración exhaustiva. Distinguir diferencias de datos de diferencias de CSS.

Antes de editar, consultar los tokens/utilities/variantes actuales. Reutilizar antes
de extender. Mantener naming y semántica. Elegir el menor diff coherente y mantenible;
no añadir overrides redundantes solo para reducir líneas modificadas.

No reemplazar stylesheets completos, duplicar componentes/clases, crear ComponentV2,
introducir un sistema visual paralelo ni usar !important como parche habitual.
No instalar dependencias cosméticas, modificar lógica de negocio ni ocultar datos,
controles, errores o elementos accesibles para que coincida la captura.
No alterar estilos globales para arreglar una pantalla. Si cambia un componente
compartido, identificar consumidores y comprobar los representativos afectados;
si el impacto excede la tarea, escalar antes de ese cambio.

## Dos pasadas, con cierre

Una pasada = un lote agrupado de edición + render y validación de todos los targets.
Desktop y mobile del mismo lote no son dos pasadas. BEFORE no consume una pasada.

1. Registrar **pasada 1 iniciada** antes de editar. Aplicar el patch agrupado.
2. Ejecutar checks locales pertinentes ya existentes; capturar AFTER-1 e inspeccionar
   target/current en las mismas condiciones. Comprobar las interacciones afectadas,
   consola y responsive. No confiar solo en una diferencia de píxeles o build verde.
3. Si se cumplen los criterios, DONE ahora. No gastar la segunda pasada por costumbre.
4. Si quedan diferencias dentro del alcance, enumerarlas en un único grupo. Registrar
   **pasada 2 iniciada**; corregir solo esos residuos y validar AFTER-2.
5. Tras la segunda, DONE únicamente si cumple. Si no, NEEDS_REVIEW con diferencias
   y capturas. Sin tercera pasada, nuevo ID ni nueva sesión para reiniciar el límite.

Toda edición posterior al lote validado inicia otra pasada. Un fallo o interrupción
después de iniciar un lote consume esa pasada. Una recaptura técnica sin editar puede
reintentarse una vez; ante el mismo bloqueo ambiental, parar. No reinstalar el entorno
ni diagnosticar infraestructura indefinidamente dentro de UI Light.

Si solo hay desktop, comparar desktop y comprobar que el mobile existente conserva
su uso y no añade overflow; no inventar un target mobile. Si hay ambos, validar ambos.
No añadir pruebas que solo repliquen CSS trivial. Reutilizar checks de interacción y
accesibilidad pertinentes; no convertir un ajuste visual en una batería nueva de tests.

## Salida y escalamiento

- **DONE:** targets y criterios cumplidos, capturas actuales, sin regresión detectada
  en las comprobaciones declaradas. Es autoverificación, no QA independiente ni permiso de push.
- **NEEDS_REVIEW:** pasadas agotadas o diferencias pendientes; conservar cambios y evidencia.
- **BLOCKED:** falta target, recurso, render, autorización o acceso necesario.
- **ESCALATE:** requiere API/auth/datos, lógica, estado complejo, arquitectura o refactor amplio.
  También puede escalar por dificultad visual aunque no cambie negocio. No activar Sol/Opus
  automáticamente; explicar el obstáculo y transferir lo aprendido sin rehacer auditorías.

Entregar en pocas líneas: estado, pasadas usadas, archivos cambiados, capturas,
checks ejecutados y pendientes. Registrar hallazgos ajenos sin implementarlos. No
commitear, pushear ni desplegar por este flujo. Conservar tareas/capturas privadamente.

Este contrato es una instrucción operativa: no impone por software el límite de tokens,
créditos, tiempo o pasadas. El contador vive en la tarea; no es un ledger inviolable.
