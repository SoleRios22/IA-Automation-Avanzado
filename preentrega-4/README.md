# Preentrega 4

## Sincronización del Cerebro Agéntico con Ecosistemas de Negocio

**Estudiante:** Soledad Ríos

### Objetivo

Extender el workflow desarrollado en módulos anteriores incorporando integraciones externas reales y controles preventivos no-code.

### Herramientas utilizadas

- n8n
- Google Gemini
- Gmail
- HubSpot CRM
- Slack
- Airtable
- Google Sheets

### Controles implementados

- IF anti auto-reply.
- Normalización del payload de Gmail.
- Search Contact en HubSpot antes de crear o actualizar.
- IF para detectar contactos existentes.
- Gmail Create Draft como Human-in-the-loop.
- Set de limpieza antes de Slack.
- Envío de notificación al canal de operaciones.

### Archivo entregado

`checkpoint4_soledad_rios.json`

El workflow puede importarse directamente en n8n.

Las credenciales OAuth2, tokens y secretos no están incluidas en el archivo y deben configurarse nuevamente en el entorno donde se importe.
