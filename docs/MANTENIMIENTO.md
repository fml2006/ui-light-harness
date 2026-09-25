# Mantenimiento y distribución

Versión actual: **0.1.1 — piloto**. Esta distribución es autónoma: puede copiarse a
un proyecto frontend sin instalar el orquestador completo. No tiene conexión automática
con su runner. El kit completo conserva una copia del módulo para distribuirlo junto
con el resto de sus herramientas.

Tomar este repositorio independiente como fuente de las reglas UI Light. Al publicar
una actualización, registrar aquí el cambio y actualizar la copia del kit completo
mediante un diff revisado. No copiar .git, capturas, tareas ni configuración particular
de una app. Las copias instaladas en proyectos tampoco se actualizan solas.

Para actualizar una app: comparar primero, integrar instrucciones y configuración sin
reemplazar las existentes y conservar su mapa EXISTING-UI, fuentes de marca, patrones,
tareas y evidencia. No volver a poner esas memorias en blanco desde la plantilla.

## 0.1.1

- Entrada explícita para Claude Code mediante CLAUDE.md e import de AGENTS.md.
- Guía común de uso, modelo separado por cliente y contador conservado al cambiar de cliente.
- Sin llamadas de prueba a modelos ni evidencia de fidelidad/ahorro todavía.

## 0.1.0

- Paquete separado para frontend, un agente y hasta dos pasadas.
- Marca heredada del sitio actual; distinción entre target e inspiración externa.
- Guía USO.md para preparación y pedidos por screenshots.
- Sin validación empírica todavía: evaluar el piloto antes de estandarizarlo para el equipo.
