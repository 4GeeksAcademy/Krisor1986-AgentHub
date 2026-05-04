# AgentHub Admin Dashboard - Especificacion funcional y visual

## Objetivo

Construir un prototipo HTML estatico para el panel interno de administracion de AgentHub, una plataforma SaaS donde empresas alquilan agentes de IA preconfigurados con distintas skills. El prototipo debe servir como referencia visual y funcional para desarrollo backend futuro.

El entregable debe funcionar sin backend, sin herramientas de build y sin frameworks JavaScript. Toda la informacion estara hardcodeada en el HTML/JavaScript.

## Restricciones tecnicas

- Usar un unico archivo `index.html` como entrada principal del prototipo.
- Cargar Tailwind CSS mediante CDN.
- Implementar toda la interactividad con JavaScript vanilla.
- No usar React, Vue, Angular, jQuery ni herramientas de build.
- No conectar con APIs ni persistir datos.
- El modo claro/oscuro debe implementarse usando la estrategia `dark:` de Tailwind y una clase `dark` aplicada al elemento `html`.
- El diseno debe ser responsive y usable en escritorio y tablet.

## Layout global

La pagina debe tener:

- Una barra lateral persistente a la izquierda con la marca `AgentHub`.
- Una barra superior dentro del area principal con titulo, contexto y toggle de modo claro/oscuro.
- Un area principal con seis secciones visibles en una sola pagina.
- Navegacion lateral con enlaces que hacen scroll a cada seccion.

Secciones de navegacion:

1. Dashboard
2. Usuarios
3. Agentes
4. Skills
5. Contrataciones
6. Log de errores

## Sistema visual

Modo claro:

- Fondo general gris claro.
- Tarjetas blancas.
- Bordes sutiles.
- Texto principal gris oscuro.
- Acentos azul/cian.

Modo oscuro:

- Fondo general gris/azul muy oscuro.
- Tarjetas oscuras.
- Bordes gris oscuro.
- Texto claro.
- Acentos azul/cian visibles.

Los componentes deben sentirse profesionales, limpios y propios de una herramienta SaaS interna.

## Datos hardcodeados

El prototipo debe incluir datos suficientes para revisar todas las secciones:

- Al menos 4 usuarios.
- Al menos 4 agentes.
- Al menos 6 skills.
- Al menos 4 contrataciones.
- Al menos 4 errores.

No se usaran APIs ni backend.

## 1. Dashboard

Debe mostrar cuatro tarjetas de metrica:

1. Ingresos totales generados este mes.
2. Perdida total por descuentos y cupones.
3. Numero de agentes activos en todos los clientes.
4. Numero de agentes actualmente marcados como fallando.

Cada tarjeta debe incluir:

- Etiqueta.
- Valor principal.
- Texto secundario.
- Color visual distintivo.

Debajo debe incluir un marcador de grafico de actividad semanal. Puede ser un grafico falso con barras hechas en HTML/CSS.

## 2. Gestion de usuarios

Debe incluir una tabla con columnas:

- Nombre
- Email
- Plan
- Estado
- Acciones

Cada fila debe tener un dropdown de acciones con boton `⋮`.

Opciones:

- Ver detalle
- Eliminar

Al hacer clic en `Ver detalle`, se abre un modal con el registro completo del usuario:

- Nombre
- Email
- Plan
- Estado
- Empresa
- Fecha de alta
- Ultimo acceso

El modal debe cerrarse con boton de cerrar y haciendo clic en el backdrop.

## 3. Gestion de agentes

Debe mostrar un listado de agentes registrados.

Cada agente debe mostrar:

- Nombre del agente
- Propietario
- Estado actual: activo, inactivo o fallando
- Lista de skills colapsada por defecto
- Dropdown de acciones

Las skills deben estar ocultas inicialmente. Al hacer clic en un control expandible, deben aparecer con una transicion suave.

Opciones del dropdown:

- Configurar
- Eliminar

`Configurar` abre un modal con el prompt de sistema completo del agente.

## 4. Skills

Debe mostrar el catalogo de skills disponibles.

Debe incluir esta explicacion:

“En AgentHub, una skill es una capacidad reutilizable que puede adjuntarse a un agente para ampliar lo que puede hacer, como navegar por la web, leer documentos o gestionar calendarios.”

Cada skill debe mostrar:

- Nombre
- Descripcion breve
- Numero de agentes que la tienen habilitada
- Dropdown de acciones

Opciones:

- Ver detalle
- Eliminar

`Ver detalle` abre un modal con informacion extendida de la skill.

## 5. Contrataciones de agentes

Debe incluir una tabla con contratos activos y pasados.

Columnas:

- Cliente
- Agente alquilado
- Skills contratadas
- Fechas del contrato
- Importe total pagado
- Acciones

Cada fila debe tener dropdown de acciones.

`Ver detalle` abre un modal con:

- Cliente
- Agente
- Periodo del contrato
- Estado del contrato
- Lista de skills contratadas
- Precio individual de cada skill
- Importe total pagado

## 6. Log de errores

Debe mostrar un registro de errores de ejecucion de agentes.

Cada entrada debe incluir:

- Timestamp
- Nombre del agente
- Tipo de error
- Descripcion breve
- Badge de gravedad o tipo
- Acciones

Gravedades sugeridas:

- Critico: rojo
- Alto: naranja/rojo
- Medio: amarillo
- Bajo: azul/gris

Opciones del dropdown:

- Ver detalle
- Marcar como resuelto

`Ver detalle` abre un modal con la traza completa del error.

`Marcar como resuelto` puede cambiar visualmente la fila o mostrar una notificacion.

## Interacciones globales

### Dropdowns

- Se abren al hacer clic en el boton `⋮`.
- Solo puede haber un dropdown abierto a la vez.
- Se cierran al hacer clic fuera.
- Las opciones deben ser botones.

### Modales

- Debe existir un sistema reutilizable de modal.
- Debe tener backdrop.
- Debe cerrarse con boton.
- Debe cerrarse haciendo clic fuera.
- Debe cerrarse con la tecla Escape.
- El contenido cambia segun la accion elegida.

### Modo claro/oscuro

- El toggle debe alternar la clase `dark` en `document.documentElement`.
- La interfaz debe usar clases `dark:` de Tailwind.
- El texto del boton debe cambiar entre modo claro y modo oscuro.

### Navegacion

- Los enlaces laterales deben hacer scroll hacia cada seccion.
- El enlace activo debe destacarse visualmente al hacer clic.

## Inventario de componentes reutilizables

El prototipo debe reutilizar los siguientes componentes de UI en varias secciones:

1. Sidebar de navegacion: menu lateral persistente con enlaces a las seis secciones principales.
2. Barra superior: contiene el titulo de la seccion activa, contexto breve y toggle de modo claro/oscuro.
3. Tarjeta de metrica: usada en el Dashboard para mostrar etiqueta, valor principal y descripcion secundaria.
4. Tabla de datos: usada en usuarios, contrataciones y log de errores.
5. Dropdown de acciones: menu contextual activado con boton `⋮`, reutilizado en usuarios, agentes, skills, contrataciones y errores.
6. Modal reutilizable: overlay con backdrop, titulo, contenido dinamico y boton de cierre.
7. Badge de estado: etiqueta visual con color segun estado o gravedad.
8. Lista colapsable de skills: componente expandible usado en la gestion de agentes.
9. Toast o notificacion breve: mensaje temporal para acciones como eliminar o marcar error como resuelto.
10. Toggle de modo oscuro: control global que alterna la clase `dark` en el elemento `html`.

## Criterios de aceptacion

El proyecto se considera completo si:

- Existe `SPECS.md`.
- `SPECS.md` esta commiteado antes de crear `index.html`.
- Existe `index.html`.
- El panel tiene las seis secciones requeridas.
- Hay navegacion lateral persistente.
- El modo claro/oscuro funciona.
- Todas las secciones usan datos hardcodeados.
- Los dropdowns funcionan.
- Los modales abren y cierran correctamente.
- Las skills de agentes estan colapsadas por defecto y se expanden.
- El dashboard muestra cuatro metricas y grafico semanal placeholder.
- Todo el JavaScript es vanilla.
- Tailwind se carga por CDN.
