# Twitter/X MCP Server para GENIA

Un servidor MCP (Model Context Protocol) para Twitter/X que permite a GENIA interactuar con tweets, mensajes directos y otros recursos de Twitter/X.

## Características

- Autenticación con API Key, API Secret, Access Token y Access Secret
- Operaciones sobre tweets y mensajes directos
- Búsqueda y análisis de tendencias
- Integración con el orquestador MCP de GENIA
- Soporte para autenticación por usuario

## Requisitos

- Node.js 16+
- NPX
- Credenciales de API de Twitter/X (API Key, API Secret, Access Token, Access Secret)

## Instalación

### Usando NPX

```bash
npx twitter-x-mcp@latest
```

### Ejecución

```bash
TWITTER_API_KEY=your_api_key \
TWITTER_API_SECRET=your_api_secret \
TWITTER_ACCESS_TOKEN=your_access_token \
TWITTER_ACCESS_SECRET=your_access_secret \
npx twitter-x-mcp@latest
```

## Operaciones Soportadas

### Timeline

- `get_home_timeline`: Obtiene la timeline del usuario
- `get_user_timeline`: Obtiene la timeline de un usuario específico
- `get_mentions_timeline`: Obtiene menciones del usuario

### Tweets

- `get_tweet`: Obtiene información de un tweet específico
- `create_tweet`: Publica un nuevo tweet
- `delete_tweet`: Elimina un tweet
- `retweet`: Retweetea un tweet
- `like_tweet`: Da like a un tweet
- `reply_to_tweet`: Responde a un tweet

### Mensajes Directos

- `get_direct_messages`: Obtiene mensajes directos
- `send_direct_message`: Envía un mensaje directo
- `delete_direct_message`: Elimina un mensaje directo

### Búsqueda y Tendencias

- `search_tweets`: Busca tweets por palabras clave
- `get_trends`: Obtiene tendencias actuales
- `get_trends_by_location`: Obtiene tendencias por ubicación

## Integración con GENIA

Este servidor MCP está diseñado para integrarse con el orquestador MCP de GENIA, permitiendo que los usuarios conecten sus propias cuentas de Twitter/X y ejecuten operaciones a través de la interfaz unificada de GENIA.

### Ejemplo de Configuración en el Orquestador

```python
orchestrator.register_server(
    name="twitter_x",
    command=["npx", "twitter-x-mcp@latest"],
    env_vars={
        "TWITTER_API_KEY": "${TWITTER_API_KEY}",
        "TWITTER_API_SECRET": "${TWITTER_API_SECRET}",
        "TWITTER_ACCESS_TOKEN": "${TWITTER_ACCESS_TOKEN}",
        "TWITTER_ACCESS_SECRET": "${TWITTER_ACCESS_SECRET}"
    }
)
```

## Manejo de Errores

El servidor incluye manejo robusto de errores para:

- Credenciales inválidas o expiradas
- Límites de API excedidos
- Recursos no encontrados
- Errores de formato en solicitudes
- Restricciones de la plataforma

Cada error incluye un código específico y un mensaje descriptivo para facilitar la depuración.

## Verificación de Dependencias

El servidor verifica automáticamente todas las dependencias necesarias al iniciar:

- Versión de Node.js
- Disponibilidad de NPX
- Validez de las credenciales de Twitter/X
- Conectividad con la API de Twitter/X

Si alguna dependencia falta o es incompatible, el servidor proporcionará instrucciones claras para resolverlo.

## Consideraciones de Seguridad

- Las credenciales de API son sensibles y deben manejarse con cuidado
- Se recomienda utilizar cuentas dedicadas para automatización
- El uso excesivo de la API puede resultar en limitaciones temporales o permanentes
- Respetar los términos de servicio de Twitter/X

## Desarrollo

### Requisitos

- Node.js 16+
- npm o yarn

### Instalación de Dependencias

```bash
npm install
```

### Compilación

```bash
npm run build
```

### Pruebas

```bash
npm test
```

## Licencia

MIT

## Autor

GENIA Team
