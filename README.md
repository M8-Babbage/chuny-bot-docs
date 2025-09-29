# Índice de Comandos (No Premium)

- Gestión de Actividades
  - [/raid](#raid)
  - [/split](#split)
  - [/status](#status)
- Gestión de Claims
  - [/claim](#claim)
- Gestión de Plantillas
  - [/template](#template)
  - [/migrate](#migrate)
- Visualización de Armas y Categorías
  - [/show_all_weapons](#show_all_weapons)
  - [/show_all_categories](#show_all_categories)
- Gestión de Economía
  - [/economy](#economy)
  - [/economy-roles](#economy-roles)
- Gestión de Roles Autorizados
  - [/roles](#roles)

---

## /raid

- Descripción
  - Envía una notificación de actividad usando una plantilla del servidor y publica un mensaje con selección de armas, botones de “Lista de espera” y “No puedo ir”, y recordatorios opcionales.
- Sintaxis
  - `/raid template:<string> time:<string(1-60)> title:<string?> description:<string?> color:<hex?> image:<url?> reminder:<string(1-60)?> roles_to_notify:<ids_comas?>`
- Permisos
  - Requiere rol autorizado en el servidor (Authorized Roles) conforme a la política del servidor. Requiere estado premium del servidor.
- Parámetros
  - `template` (obligatorio): nombre de la plantilla.
  - `time` (obligatorio): minutos restantes (1–60).
  - `title` (opcional): título personalizado.
  - `description` (opcional): descripción del evento.
  - `color` (opcional): color del embed en formato `#RRGGBB`.
  - `image` (opcional): URL de imagen para el embed.
  - `reminder` (opcional): minutos antes para enviar recordatorio (1–60).
  - `roles_to_notify` (opcional): IDs de roles a mencionar, separados por coma.
- Ejemplos
  - `/raid template:Avalon time:45 title:"Avalon Roam" color:#00FFFF reminder:10`
- Errores y soluciones
  - `Plantilla No Encontrada`: verifica el nombre o crea una nueva plantilla.
  - `Error en el Tiempo del Evento`: usa valores 1–60.
  - `Acceso denegado`: solicita a un admin agregarte a roles autorizados.

---

## /split

- Descripción
  - Divide a los participantes de un evento en grupos o roles definidos (si aplica), optimizando la organización.
- Sintaxis
  - `/split`
- Permisos
  - Normalmente administradores/autorizados según política del servidor.
- Parámetros
  - Sin parámetros obligatorios.
- Ejemplos
  - `/split`
- Errores y soluciones
  - `Permisos insuficientes`: solicita rol autorizado o apoyo de admin.

---

## /status

- Descripción
  - Muestra información general del bot y estado del sistema.
- Sintaxis
  - `/status`
- Permisos
  - Disponible para usuarios del servidor.
- Parámetros
  - Sin parámetros.
- Ejemplos
  - `/status`
- Errores y soluciones
  - `Error interno`: reintenta o contacta a un administrador.

---

## /claim

- Descripción
  - Gestiona claims (reservas) de actividades: creación, cancelación, completado y configuración automática de canales.
- Sintaxis
  - Subcomandos:
    - `create actividad:<string> mapa:<string> tiempo:<string> descripcion:<string?>`
    - `cancel claim_id:<string>`
    - `complete claim_id:<string>`
    - `setup`
- Permisos
  - `create`: disponible para todos.
  - `cancel/complete`: usuario estándar sobre sus propios claims; roles autorizados y administradores sobre cualquier claim.
  - `setup`: administradores o roles autorizados.
- Parámetros
  - `create`:
    - `actividad` (obligatorio)
    - `mapa` (obligatorio)
    - `tiempo` (obligatorio, ej: `1h 30m`, `45m`)
    - `descripcion` (opcional)
  - `cancel` / `complete`:
    - `claim_id` (obligatorio)
  - `setup`: sin parámetros; crea categoría `claims` y canales por defecto.
- Ejemplos
  - `/claim create actividad:"Orbe de Poder" mapa:"Caerleon" tiempo:"45m"`
  - `/claim cancel claim_id:ABC123`
  - `/claim complete claim_id:ABC123`
  - `/claim setup`
- Errores y soluciones
  - `Configuración Incompleta`: ejecuta `/claim setup` para crear canales.
  - `No tienes permisos`: valida si eres autor del claim o solicita rol autorizado/admin.

---

## /template

- Descripción
  - Editor integral de plantillas de actividades (armas, roles, descripción, etc.).
- Sintaxis (acciones comunes)
  - `/template` (abre el editor y navegación por botones/menus)
- Permisos
  - Usualmente administradores o roles autorizados (según servidor).
- Parámetros
  - Se gestionan vía componentes (botones/select/modals) dentro del editor.
- Ejemplos
  - `/template` → editar categorías/armas, actualizar título/descr.
- Errores y soluciones
  - `Acceso denegado`: solicita rol autorizado/admin.
  - `Datos inválidos`: revisa formatos y límites mostrados por el sistema.

---

## /migrate

- Descripción
  - Migra o adapta información/configuración del sistema a versiones nuevas.
- Sintaxis
  - `/migrate`
- Permisos
  - Normalmente administradores/autorizados.
- Parámetros
  - Sin parámetros.
- Ejemplos
  - `/migrate`
- Errores y soluciones
  - `Permisos insuficientes`: solicita asistencia de un administrador.

---

## /show_all_weapons

- Descripción
  - Muestra un listado de todas las armas disponibles configuradas en el sistema.
- Sintaxis
  - `/show_all_weapons`
- Permisos
  - Visibilidad según políticas del servidor (típicamente administradores/autorizados).
- Parámetros
  - Sin parámetros.
- Ejemplos
  - `/show_all_weapons`
- Errores y soluciones
  - `No hay armas`: verifica la carga de datos o contacto admin.

---

## /show_all_categories

- Descripción
  - Muestra todas las categorías de armas configuradas.
- Sintaxis
  - `/show_all_categories`
- Permisos
  - Visibilidad según políticas del servidor.
- Parámetros
  - Sin parámetros.
- Ejemplos
  - `/show_all_categories`
- Errores y soluciones
  - `Sin categorías`: valida configuración o contacto admin.

---

## /economy

- Descripción
  - Gestiona balances y operaciones económicas del servidor, incluyendo cálculo de regear desde imágenes.
- Sintaxis (subcomandos)
  - `add usuario:<user> cantidad:<int> razon:<string?>`
  - `remove usuario:<user> cantidad:<int> razon:<string?>`
  - `balance usuario:<user?>`
  - `top cantidad:<int?>`
  - `regear image:<attachment> user:<user?>`
- Permisos
  - Requiere roles de economía según el subcomando:
    - `add`: `ECONOMY_ADD` o `ECONOMY`
    - `remove`: `ECONOMY_REMOVE` o `ECONOMY`
    - `balance`: ver propio balance libre; ver ajeno requiere `ECONOMY_VIEW` o `ECONOMY`
    - `top`: `ECONOMY_VIEW` o `ECONOMY`
    - `regear`: `ECONOMY`
- Parámetros
  - `add/remove`: `usuario` (obligatorio), `cantidad` (obligatorio 1–999999999), `razon` (opcional)
  - `balance`: `usuario` (opcional; si no, muestra el propio)
  - `top`: `cantidad` (opcional 1–20)
  - `regear`: `image` (obligatorio), `user` (opcional)
- Ejemplos
  - `/economy add usuario:@User cantidad:500 razon:"Recompensa"`
  - `/economy remove usuario:@User cantidad:100 razon:"Multa"`
  - `/economy balance` (propio) / `/economy balance usuario:@User` (ajeno)
  - `/economy top cantidad:10`
  - `/economy regear image:<captura> user:@User`
- Errores y soluciones
  - `Permisos de Economía Insuficientes`: solicita el rol correspondiente.
  - `Imagen requerida (regear)`: adjunta una imagen clara del set.
  - `API de precios sin datos`: reintenta o usa otra ciudad/atributos.

---

## /economy-roles

- Descripción
  - Gestiona roles con permisos de economía: alta, baja, listado, sincronización, etc.
- Sintaxis (subcomandos comunes)
  - `add rol:<role> permisos:<string> descripcion:<string?>`
  - `remove rol:<role>`
  - `list`
  - `sync`
  - `clear`
  - `stats`
- Permisos
  - Administradores/propietario, según políticas del servidor.
- Parámetros
  - `add`: `rol` (obligatorio), `permisos` (obligatorio: `ECONOMY_ADD|ECONOMY_REMOVE|ECONOMY_VIEW|ECONOMY_ADMIN|ALL`), `descripcion` (opcional)
  - `remove`: `rol` (obligatorio)
  - `list/sync/clear/stats`: sin parámetros.
- Ejemplos
  - `/economy-roles add rol:@Economy permisos:ECONOMY_VIEW`
  - `/economy-roles list`
- Errores y soluciones
  - `Servidor sin premium/roles`: valida políticas del servidor y ajusta roles.

---

## /roles

- Descripción
  - Gestiona roles autorizados del servidor (alta/baja/lista). Estos roles habilitan comandos de operación (como /raid) sin ser administradores.
- Sintaxis (subcomandos comunes)
  - `add rol:<role>`
  - `remove rol:<role>`
  - `list`
- Permisos
  - Administradores/propietario.
- Parámetros
  - `add/remove`: `rol` (obligatorio)
  - `list`: sin parámetros.
- Ejemplos
  - `/roles add rol:@Autorizado`
  - `/roles list`
- Errores y soluciones
  - `Rol no encontrado`: verifica que el rol existe en tu servidor.

---

# Notas Generales de Error

- `Acceso Denegado` / `Permisos Insuficientes`
  - Solicita al administrador que te asigne el rol requerido.
- `Formato Inválido`
  - Revisa la sintaxis exacta descrita en cada comando.
- `Recursos no encontrados`
  - Verifica nombres y existencia en el servidor (plantillas, roles, claims).
