# 📚 Documentación Oficial de Comandos - Chuny Bot

## 🔐 Sistema de Permisos

### Tipos de Permisos
- **🟠 Administrador**: Administradores del servidor de Discord
- **🟡 Premium**: Servidores con estado premium
- **🔵 Roles Autorizados**: Roles configurados para notificaciones
- **🟢 Roles de Gremio**: Roles de gremio/alianza configurados
- **🟣 Roles de Economía**: Roles con permisos específicos de economía
- **⚪ Público**: Disponible para todos los usuarios

---

## 📋 Lista Completa de Comandos

### 🎯 `/raid` - Crear Notificaciones de Actividades
**Descripción**: Envía notificaciones para actividades usando plantillas del servidor

**Permisos Requeridos**: 🟡 Premium + 🔵 Roles Autorizados

**Opciones**:
- `template` (obligatorio): Plantilla a usar para la actividad
- `time` (obligatorio): Tiempo restante en minutos (1-60)
- `title` (opcional): Título personalizado
- `description` (opcional): Descripción personalizada
- `color` (opcional): Color del embed en formato hexadecimal (#FFFFFF)
- `image` (opcional): URL de imagen para el embed
- `reminder` (opcional): Minutos antes para recordatorio (1-60)
- `roles_to_notify` (opcional): IDs de roles a notificar separados por comas

**Ejemplo de uso**:
```
/raid template:Avalonian_Dungeon time:30 title:Dungeon T8.3 description:Necesitamos tank y healer reminder:10
```

---

### 🏛️ `/template` - Gestión de Plantillas
**Descripción**: Sistema completo para gestionar plantillas de actividades

**Permisos Requeridos**: 🟡 Premium + 🔵 Roles Autorizados

#### Subcomandos:

**`/template create`**
- Inicia el asistente de creación de plantillas
- Proceso interactivo paso a paso

**`/template edit`**
- `name` (obligatorio): Nombre de la plantilla a editar
- Sistema de edición interactivo con menús

**`/template list`**
- Lista todas las plantillas disponibles en el servidor

**`/template clone`**
- `source` (obligatorio): Plantilla origen a clonar
- `new_name` (obligatorio): Nombre para la nueva plantilla

**`/template delete`**
- `name` (obligatorio): Nombre de la plantilla a eliminar

**`/template export`**
- `name` (obligatorio): Plantilla a exportar
- Genera archivo JSON descargable

**`/template import`**
- `file` (obligatorio): Archivo JSON de plantilla
- `name` (obligatorio): Nombre para la plantilla importada

**`/template rename`**
- `name` (obligatorio): Plantilla actual a renombrar
- `new_name` (obligatorio): Nuevo nombre

**Ejemplo de uso**:
```
/template create
/template edit name:Avalonian_Dungeon
/template clone source:Dungeon_Base new_name:Dungeon_T8
```

---

### 💰 `/economy` - Sistema de Economía
**Descripción**: Gestiona la economía del servidor con sistema de dinero virtual

**Permisos Requeridos**: 🟡 Premium + 🟣 Roles de Economía

#### Subcomandos:

**`/economy add`**
- `usuario` (obligatorio): Usuario al que añadir dinero
- `cantidad` (obligatorio): Cantidad a añadir (1-999,999,999)
- `razon` (opcional): Razón para añadir el dinero (máx. 200 caracteres)
- **Permiso específico**: ECONOMY_ADD

**`/economy remove`**
- `usuario` (obligatorio): Usuario al que quitar dinero
- `cantidad` (obligatorio): Cantidad a quitar (1-999,999,999)
- `razon` (opcional): Razón para quitar el dinero (máx. 200 caracteres)
- **Permiso específico**: ECONOMY_REMOVE

**`/economy balance`**
- `usuario` (opcional): Usuario del que ver el balance
- Si no se especifica, muestra el balance propio
- **Permiso específico**: ECONOMY_VIEW + 🟢 Roles de Gremio

**`/economy top`**
- `cantidad` (opcional): Número de usuarios a mostrar (1-20, por defecto 10)
- **Permiso específico**: ECONOMY_VIEW + 🟢 Roles de Gremio

**Ejemplo de uso**:
```
/economy add usuario:@Juan cantidad:1000 razon:Recompensa por evento
/economy balance usuario:@María
/economy top cantidad:15
```

---

### 🏰 `/guilds` - Gestión de Roles de Gremio
**Descripción**: Administra roles de gremio/alianza para permisos especiales

**Permisos Requeridos**: 🟠 Administrador

#### Subcomandos:

**`/guilds add`**
- `role` (obligatorio): Rol a añadir como rol de gremio

**`/guilds remove`**
- `role` (obligatorio): Rol a eliminar de roles de gremio

**`/guilds list`**
- Lista todos los roles de gremio configurados
- Limpia automáticamente roles obsoletos

**Ejemplo de uso**:
```
/guilds add role:@Gremio_Principal
/guilds remove role:@Gremio_Inactivo
/guilds list
```

---

### 🎭 `/roles` - Gestión de Roles Autorizados
**Descripción**: Gestiona roles autorizados para enviar notificaciones

**Permisos Requeridos**: 🟡 Premium + 🟠 Administrador

#### Subcomandos:

**`/roles add`**
- `role` (obligatorio): Rol a autorizar para notificaciones

**`/roles remove`**
- `role` (obligatorio): Rol a desautorizar

**`/roles list`**
- Lista todos los roles autorizados

**`/roles clear`**
- Elimina todos los roles autorizados del servidor

**Ejemplo de uso**:
```
/roles add role:@Creadores_Contenido
/roles remove role:@Rol_Temporal
/roles list
```

---

### 💎 `/economy-roles` - Gestión de Roles de Economía
**Descripción**: Administra roles con permisos específicos del sistema de economía

**Permisos Requeridos**: 🟡 Premium + 🟠 Administrador

#### Subcomandos:

**`/economy-roles add`**
- `rol` (obligatorio): Rol a autorizar para economía
- `permisos` (opcional): Permisos específicos a otorgar
  - `ECONOMY`: Permisos básicos
  - `ECONOMY_ADD`: Añadir dinero
  - `ECONOMY_REMOVE`: Eliminar dinero
  - `ECONOMY_VIEW`: Ver balances
  - `ECONOMY_ADMIN`: Administrador completo
  - `ALL`: Todos los permisos
- `descripcion` (opcional): Descripción del rol (máx. 500 caracteres)

**`/economy-roles remove`**
- `rol` (obligatorio): Rol a desautorizar

**`/economy-roles list`**
- Lista todos los roles de economía autorizados

**`/economy-roles sync`**
- Sincroniza roles con Discord (elimina roles inexistentes)

**`/economy-roles clear`**
- Elimina todos los roles de economía del servidor

**`/economy-roles stats`**
- Muestra estadísticas de roles de economía

**Ejemplo de uso**:
```
/economy-roles add rol:@Tesoreros permisos:ECONOMY_ADD descripcion:Encargados de recompensas
/economy-roles list
/economy-roles sync
```

---

### 🎯 `/claim` - Sistema de Claims
**Descripción**: Sistema para apartar actividades y recursos de Albion Online

**Permisos Requeridos**: ⚪ Público (crear) / 🟠 Administrador + 🔵 Roles Autorizados + 🟢 Roles de Gremio (gestionar)

#### Subcomandos:

**`/claim create`**
- `actividad` (obligatorio): Tipo de actividad (máx. 100 caracteres)
- `mapa` (obligatorio): Mapa donde se realizará (máx. 100 caracteres)
- `tiempo` (obligatorio): Tiempo hasta completar (ej: 1h 30m, 45m)
- `descripcion` (opcional): Descripción adicional (máx. 500 caracteres)

**`/claim complete`**
- `claim_id` (obligatorio): ID del claim a completar
- Solo el creador, administradores, roles autorizados o roles de gremio

**`/claim cancel`**
- `claim_id` (obligatorio): ID del claim a cancelar
- Solo el creador, administradores, roles autorizados o roles de gremio

**`/claim setup`**
- Configura automáticamente categoría y canales para claims
- **Permiso específico**: 🟠 Administrador

**Ejemplo de uso**:
```
/claim create actividad:Orbe de Poder T8 mapa:Caerleon tiempo:2h descripcion:Necesitamos 20 personas
/claim complete claim_id:CLAIM_ABC123
/claim cancel claim_id:CLAIM_XYZ789
```

---

### 🔍 `/decode` - Decodificador Misterioso
**Descripción**: Decodifica información usando herramienta misteriosa desde archivos

**Permisos Requeridos**: 🔍 Usuarios Autorizados

**Opciones**:
- `archivo` (obligatorio): Archivo .txt/.dat con datos hexadecimales

**Ejemplo de uso**:
```
/decode archivo:[adjuntar_archivo.txt]
```

---

### 💸 `/split` - Calculadora de División de Botín
**Descripción**: Calcula división de botín entre jugadores con impuestos

**Permisos Requeridos**: 🟡 Premium

**Opciones**:
- `motivo` (obligatorio): Motivo de la división (máx. 100 caracteres)
- `cantidad_total` (obligatorio): Cantidad total a dividir (mínimo 1)
- `jugadores` (obligatorio): Número de jugadores (2-20)
- `tax` (opcional): Porcentaje de impuesto (0-50%)

**Ejemplo de uso**:
```
/split motivo:Dungeon T8.3 cantidad_total:5000000 jugadores:5 tax:15
```

---

### ⚔️ `/show_all_weapons` - Lista de Armas
**Descripción**: Muestra todas las armas disponibles en la base de datos

**Permisos Requeridos**: 🟡 Premium

**Sin opciones adicionales**

**Ejemplo de uso**:
```
/show_all_weapons
```

---

### 📂 `/show_all_categories` - Lista de Categorías
**Descripción**: Muestra todas las categorías de armas disponibles

**Permisos Requeridos**: 🟡 Premium

**Sin opciones adicionales**

**Ejemplo de uso**:
```
/show_all_categories
```

---

### 📊 `/status` - Estado del Sistema
**Descripción**: Información de estado del servidor y plantillas

**Permisos Requeridos**: ⚪ Público

**Sin opciones adicionales**

**Ejemplo de uso**:
```
/status
```

---

## 🔧 Configuración Inicial Recomendada

### Para Administradores de Servidor:

1. **Configurar Premium**: Contactar al propietario del bot para activar premium
2. **Configurar Roles Autorizados**: 
   ```
   /roles add role:@Creadores_Contenido
   ```
3. **Configurar Roles de Gremio** (opcional):
   ```
   /guilds add role:@Gremio_Principal
   ```
4. **Configurar Sistema de Economía** (opcional):
   ```
   /economy-roles add rol:@Tesoreros permisos:ALL
   ```
5. **Configurar Sistema de Claims** (opcional):
   ```
   /claim setup
   ```
6. **Crear Plantillas**:
   ```
   /template create
   ```

### Para Usuarios Regulares:

1. **Ver estado del servidor**:
   ```
   /status
   ```
2. **Crear claims de actividades**:
   ```
   /claim create actividad:Dungeon T7 mapa:Thetford tiempo:1h
   ```
3. **Ver balance personal** (si tienes permisos):
   ```
   /economy balance
   ```

---

## ⚠️ Notas Importantes

- **Premium**: Muchos comandos requieren que el servidor tenga estado premium
- **Permisos Acumulativos**: Algunos comandos requieren múltiples tipos de permisos
- **Administradores**: Los administradores de Discord tienen permisos elevados en la mayoría de comandos
- **Roles de Gremio**: Proporcionan permisos adicionales para economía y gestión de claims
- **Autocompletado**: Muchos comandos incluyen autocompletado para facilitar su uso

---

## 🆘 Soporte

Si encuentras problemas con algún comando:
1. Verifica que tienes los permisos necesarios
2. Asegúrate de que el servidor tiene premium (si es requerido)
3. Contacta a un administrador del servidor
4. Como último recurso, contacta al propietario del bot

---

*Documentación generada automáticamente - Versión 1.0*
