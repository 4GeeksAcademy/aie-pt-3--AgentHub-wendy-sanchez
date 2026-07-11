# SPECS — Panel de Administración AgentHub

## 1) Descripción del producto

**AgentHub** es un prototipo de panel de administración web para supervisar, organizar y operar agentes de IA alquilables por clientes. El producto permite visualizar métricas de negocio, administrar usuarios, gestionar agentes y skills, revisar contratos y monitorear errores operativos desde una sola interfaz.

**Usuario administrador objetivo:**
- Operador interno de la plataforma (equipo de operaciones o customer success).
- Necesita auditar estado de agentes y contratos sin salir del panel.
- Toma decisiones rápidas sobre incidencias, configuración y limpieza de datos (eliminar, marcar, revisar detalle).

## 2) Stack tecnológico y restricciones

- **Estructura:** HTML semántico en una sola página tipo dashboard (puede usar secciones con `id` para navegación interna).
- **Estilos:** Tailwind CSS cargado **vía CDN**; se deben usar utilidades de Tailwind para layout, espaciado, tipografía y estados visuales.
- **Interactividad:** JavaScript **vanilla** (ES6+) para dropdowns, modales, colapsables y cambio de tema.
- **Modo oscuro:** Implementado con `dark:` de Tailwind mediante toggle global en la barra superior (por ejemplo, alternando clase `dark` en `html` o `body`).
- **Sin frameworks:** No usar React, Vue, Angular, Svelte, Alpine ni librerías UI externas.
- **Sin backend:** No hay API ni persistencia remota; todos los datos son hardcodeados de forma local.
- **Sin build tooling obligatorio:** Debe funcionar abriendo el HTML en navegador (o servido estáticamente).

## 3) Especificaciones por sección

La UI debe exponer **seis secciones** accesibles desde una navegación lateral persistente.

### 3.1 Dashboard

1. **Tarjetas de métricas (4 items):**
   - Componente: cuadrícula responsive de tarjetas.
   - Contenido por tarjeta: icono, etiqueta y valor hardcodeado.
   - Métricas obligatorias: ingresos totales del mes, pérdida total por descuentos/cupones, agentes activos, agentes fallando.
   - Comportamiento: en móvil se apilan (1 columna) y en desktop se distribuyen mínimo en 2x2.

2. **Jerarquía visual por tipo de métrica:**
   - Cada tarjeta usa un color de acento distinto (ej. verde, ámbar, azul, rojo) coherente con el significado.
   - Deben incluir fondo contrastado en claro/oscuro y sombra sutil para separación.
   - El valor numérico debe tener mayor peso tipográfico que la etiqueta.

3. **Placeholder de gráfico semanal:**
   - Debajo de las tarjetas, bloque de ancho completo con borde discontinuo y etiqueta centrada.
   - Texto mínimo: “Actividad semanal (placeholder)”.
   - Altura mínima definida para reservar espacio visual de gráfico.

### 3.2 Gestión de usuarios

1. **Tabla de usuarios registrados:**
   - Columnas obligatorias: nombre, email, plan, estado.
   - Debe mostrar al menos 5 filas hardcodeadas con variación de plan/estado.
   - Encabezados fijos y legibles en ambos modos (claro/oscuro).

2. **Dropdown de acciones por fila (⋮):**
   - Botón de activación tipo icono vertical `⋮` por cada usuario.
   - Menú con al menos dos opciones: “Ver detalle” y “Eliminar”.
   - Comportamiento: abrir/cerrar por clic, cerrar al hacer clic fuera, y solo un dropdown abierto a la vez.

3. **Modal de detalle de usuario:**
   - “Ver detalle” abre un modal overlay centrado con registro completo (campos adicionales como ID, fecha alta, último acceso).
   - Debe incluir botón visible de cierre.
   - También debe cerrarse al hacer clic en backdrop o con tecla `Escape`.

### 3.3 Gestión de agentes

1. **Listado de agentes con estado:**
   - Cada fila/tarjeta de agente muestra: nombre, propietario, estado actual.
   - Estados permitidos: activo, inactivo, fallando.
   - Estado presentado con badge visualmente diferenciado por color.

2. **Lista de skills colapsable por agente:**
   - Las skills están ocultas por defecto.
   - Control expandible (botón/flecha) revela la lista con transición suave de altura/opacidad.
   - El control debe indicar estado expandido/colapsado (rotación de ícono o texto dinámico).

3. **Dropdown de acciones + modal de configuración:**
   - Cada agente tiene menú `⋮` con “Configurar” y “Eliminar”.
   - “Configurar” abre modal con el prompt de sistema del agente en bloque legible (scroll si excede alto).
   - Modal reutiliza reglas de cierre consistentes (botón, backdrop, `Escape`).

### 3.4 Skills

1. **Encabezado explicativo de contexto:**
   - Incluir texto breve explicando que una “skill” es una capacidad modular que puede adjuntarse a múltiples agentes.
   - Debe aparecer al inicio de la sección como bloque informativo destacado.
   - El texto debe ser visible y legible en claro/oscuro.

2. **Catálogo de skills:**
   - Cada skill muestra: nombre, descripción breve, contador de agentes habilitados.
   - Mostrar al menos 6 skills hardcodeadas con contadores distintos.
   - El contador debe presentarse como badge/chip numérico.

3. **Dropdown de acciones por skill:**
   - Menú `⋮` con “Ver detalle” y “Eliminar”.
   - “Ver detalle” abre modal con información extendida (casos de uso, parámetros simulados o notas).
   - “Eliminar” queda como acción visual (sin persistencia real), pero debe reflejar feedback inmediato en UI (por ejemplo, toast o mensaje temporal).

### 3.5 Contrataciones de agentes

1. **Tabla de contratos activos y pasados:**
   - Columnas obligatorias: cliente, agente alquilado, skills contratadas, fechas del contrato, importe total pagado.
   - Debe incluir ejemplos de contratos activos y finalizados.
   - Las fechas deben mostrarse en formato consistente (ej. `YYYY-MM-DD`).

2. **Representación de skills contratadas en tabla:**
   - En cada fila, skills visibles como lista corta o chips truncados con “+N”.
   - Debe mantenerse legibilidad sin romper layout en móvil.
   - Tooltip o texto alterno opcional para nombres completos.

3. **Modal de desglose completo de contrato:**
   - Acción “Ver detalle” del dropdown abre modal con detalle integral.
   - Debe incluir lista desglosada de skills y precio individual por skill.
   - Debe mostrar subtotal de skills y total final pagado (hardcodeado, coherente visualmente).

### 3.6 Log de errores

1. **Registro tabular de errores:**
   - Campos obligatorios: timestamp, nombre del agente, tipo de error, descripción breve.
   - Debe mostrar al menos 8 errores simulados con distintos tipos.
   - Orden visual descendente por fecha/hora (más reciente arriba).

2. **Badges por tipo/gravedad:**
   - Cada error usa badge con código de color (ej. crítico=rojo, warning=ámbar, info=azul).
   - El estilo del badge debe ser consistente con otros badges del sistema.
   - Debe mantener contraste suficiente en modo claro y oscuro.

3. **Dropdown de acciones por error:**
   - Menú `⋮` con “Ver detalle” y “Marcar como resuelto”.
   - “Ver detalle” abre modal con traza completa del error (`stack trace` hardcodeado en bloque monoespaciado).
   - “Marcar como resuelto” cambia estado visual del registro (atenuado, badge “resuelto” o similar).

## 4) Inventario de componentes reutilizables UI

- **Sidebar persistente:** navegación principal con enlaces a las 6 secciones.
- **Topbar:** incluye título contextual y toggle de modo oscuro.
- **Tarjeta de métrica:** icono + etiqueta + valor + color de acento.
- **Dropdown de acciones (`⋮`):** activador, menú flotante, opciones por contexto.
- **Modal overlay reutilizable:** cabecera, contenido dinámico, cierre por botón/backdrop/`Escape`.
- **Badge de estado/tipo:** variantes para estado de agente, plan, gravedad y resolución.
- **Lista de skills colapsable:** panel expandible con animación suave.
- **Tabla responsive reutilizable:** encabezados consistentes, filas con acciones.
- **Toggle de modo oscuro:** control binario que impacta toda la interfaz con clases `dark:`.
- **Feedback temporal (toast/mensaje inline):** para acciones no persistentes como “Eliminar”.

## 5) Criterios de aceptación

1. La navegación lateral permanece visible durante toda la interacción y permite acceder a las seis secciones sin recargar la página.
2. Existe un toggle en la barra superior que alterna completamente entre tema claro y oscuro usando utilidades `dark:` de Tailwind.
3. El Dashboard muestra exactamente cuatro tarjetas de métricas con icono, etiqueta y valor hardcodeado, además de un placeholder de gráfico semanal de ancho completo.
4. La sección de Usuarios presenta tabla con columnas nombre, email, plan y estado, y cada fila incluye dropdown `⋮` funcional.
5. El dropdown de acciones se cierra al hacer clic fuera y no permite más de un menú abierto simultáneamente.
6. En Usuarios, “Ver detalle” abre modal con datos ampliados y el modal se puede cerrar por botón, backdrop y tecla `Escape`.
7. La sección de Agentes muestra nombre, propietario, estado y skills colapsadas por defecto en cada registro.
8. La interacción colapsable de skills en Agentes revela/oculta contenido con transición suave y señal visual de estado expandido.
9. En Agentes, la opción “Configurar” abre un modal con el prompt de sistema del agente en formato legible.
10. La sección Skills incluye explicación visible de qué es una skill, catálogo con nombre, descripción y contador de agentes por skill.
11. En Skills, el dropdown incluye “Ver detalle” y “Eliminar”, y “Eliminar” produce feedback visual inmediato aunque no haya persistencia.
12. La sección Contrataciones muestra tabla con cliente, agente, skills, fechas e importe total, incluyendo contratos activos y pasados.
13. En Contrataciones, “Ver detalle” abre modal con desglose completo del contrato y precios individuales por skill.
14. El Log de errores muestra timestamp, agente, tipo y descripción; cada entrada usa badges de color por gravedad/tipo.
15. En Log de errores, “Ver detalle” abre modal con stack trace completo y “Marcar como resuelto” actualiza el estado visual de la fila.
16. Todos los componentes interactivos (dropdown, modal, colapsable, toggle oscuro) funcionan con JavaScript vanilla, sin librerías adicionales.
17. El prototipo conserva legibilidad y estructura responsive en móvil y desktop.
