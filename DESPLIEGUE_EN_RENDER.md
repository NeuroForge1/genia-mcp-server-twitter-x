# Despliegue en Render

Este documento proporciona instrucciones detalladas para desplegar este servidor MCP en Render.

## Requisitos previos

- Una cuenta en [Render](https://render.com/)
- Acceso al repositorio de GitHub

## Pasos para el despliegue

1. Inicia sesión en tu cuenta de Render: https://dashboard.render.com/

2. Haz clic en "New" y selecciona "Web Service"

3. Conecta con el repositorio de GitHub:
   - Selecciona "GitHub" como proveedor de Git
   - Busca y selecciona este repositorio

4. Configura el servicio:
   - **Nombre**: Elige un nombre descriptivo (ej. `genia-mcp-server-twitter-x`)
   - **Entorno**: Docker
   - **Región**: Selecciona la región más cercana a tus usuarios
   - **Plan**: Starter (o el plan que se ajuste a tus necesidades)

5. Configura las variables de entorno:
   - Haz clic en "Advanced" y luego en "Add Environment Variable"
   - Añade las variables `TWITTER_API_KEY`, `TWITTER_API_SECRET`, `TWITTER_ACCESS_TOKEN` y `TWITTER_ACCESS_SECRET` con tus credenciales de Twitter/X
   - Estas credenciales deben tener los permisos adecuados para las operaciones que deseas realizar

6. Haz clic en "Create Web Service"

## Variables de entorno requeridas

| Variable | Descripción |
|----------|-------------|
| `TWITTER_API_KEY` | API Key de Twitter/X |
| `TWITTER_API_SECRET` | API Secret de Twitter/X |
| `TWITTER_ACCESS_TOKEN` | Access Token de Twitter/X |
| `TWITTER_ACCESS_SECRET` | Access Secret de Twitter/X |

## Verificación del despliegue

Una vez desplegado, puedes verificar que el servicio está funcionando correctamente:

1. Espera a que el estado cambie a "Live"
2. Haz clic en la URL proporcionada por Render
3. Deberías ver un mensaje indicando que el servidor MCP está en funcionamiento

## Integración con GENIA

Para integrar este servidor MCP con el orquestador de GENIA, añade la URL del servicio desplegado en Render como valor para la variable de entorno `TWITTER_X_MCP_URL` en tu despliegue de GENIA.

## Solución de problemas

Si encuentras algún problema durante el despliegue:

1. Verifica que el Dockerfile esté presente en la raíz del repositorio
2. Asegúrate de que las variables de entorno estén correctamente configuradas
3. Revisa los logs del servicio en Render para identificar posibles errores

## Soporte

Si necesitas ayuda adicional, contacta al equipo de GENIA o crea un issue en este repositorio.
