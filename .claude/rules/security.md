# Reglas de seguridad — Livix Workspace

## Reglas absolutas (nunca se rompen)

### 1. Credenciales
- **Nunca mostrar** el contenido de `.env` en el chat
- **Nunca sugerir** mostrar el contenido de `.env`
- **Nunca incluir** valores reales de API keys, tokens o contrasenas en ningun output
- Si necesitas verificar que una variable esta seteada, usar: `echo "Variable seteada: $([ -n "$VAR" ] && echo si || echo no)"`

### 2. Archivos sensibles protegidos
Los siguientes archivos nunca deben ser mostrados, subidos o incluidos en outputs:
- `.env` y cualquier variante (`.env.local`, `.env.production`)
- `token.json`
- `credentials.json`, `*_service_account.json`
- Cualquier archivo que contenga claves privadas o tokens de acceso

### 3. Acciones destructivas
Siempre pedir confirmacion explicita antes de:
- Eliminar archivos o directorios
- Resetear bases de datos
- Hacer push a ramas de produccion (main/master)
- Modificar datos de produccion en Supabase
- Eliminar registros en Supabase
- Ejecutar migraciones destructivas

---

## Reglas de operacion segura

### Antes de ejecutar comandos Bash
1. Toca datos de produccion? → Pedir confirmacion
2. Es reversible? → Si no lo es, avisar explicitamente
3. Incluye credenciales en el comando? → No ejecutar, buscar alternativa

### Al trabajar con APIs
- Siempre usar variables de entorno, nunca hardcodear keys
- Verificar que estas en entorno de desarrollo antes de operaciones de escritura
- Ante duda sobre entorno (dev vs prod), preguntar antes de ejecutar

### Al generar codigo
- Usar `process.env.VARIABLE` o equivalente, nunca strings literales de keys
- No incluir valores reales en ejemplos de codigo aunque parezcan ficticios

---

## Incidentes de seguridad

Si detectas que se ha expuesto alguna credencial accidentalmente:
1. Avisar inmediatamente al equipo
2. No incluir la credencial expuesta en ningun mensaje de seguimiento
3. Recomendar: rotar la API key inmediatamente en la plataforma correspondiente
4. Verificar que el `.env` esta en el `.gitignore` y no fue pusheado
