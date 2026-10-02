# IA Automation Avanzado

Repositorio académico correspondiente al curso **IA Automation Avanzado**.

**Estudiante:** Soledad Ríos

Este repositorio reúne las prácticas, workflows, preentregas y entrega final desarrolladas durante el curso.

El caso práctico utilizado como proyecto integrador es **Doña Ríos - Almacén Saludable**, una tienda online de Río Cuarto, Córdoba.

## Proyecto integrador

El objetivo general es desarrollar y evolucionar un sistema de automatización para la atención comercial de Doña Ríos.

A lo largo de los módulos se incorporan progresivamente:

- agentes de IA;
- clasificación de consultas;
- arquitectura multi-agente;
- memoria persistente;
- Google Sheets;
- Gmail;
- Airtable;
- CRM;
- Slack;
- controles preventivos;
- Human-in-the-loop;
- integraciones mediante OAuth2.

## Organización del repositorio

Cada módulo o preentrega se encuentra organizado en una carpeta independiente.

### Preentrega 1

Implementación inicial del agente de atención comercial.

### Preentrega 2

Arquitectura multi-agente mediante Manager y Workers.

### Preentrega 3

Incorporación de memoria persistente y contexto mediante Airtable y Simple Memory.

### Preentrega 4

Sincronización del sistema agéntico con herramientas externas reales.

Integraciones utilizadas:

- Gmail
- HubSpot CRM
- Slack
- Google Gemini
- n8n

Controles implementados:

- filtro anti auto-reply;
- búsqueda de contactos antes de crear registros en el CRM;
- prevención de duplicados;
- creación de borradores de Gmail para revisión humana;
- limpieza de payload antes de Slack;
- permisos OAuth2 bajo criterio de mínimo privilegio.

Archivo principal:

`preentrega-4/checkpoint4_soledad_rios.json`

## Importación en n8n

Para importar un workflow:

1. Descargar el archivo `.json`.
2. Abrir n8n.
3. Seleccionar **Import from File**.
4. Elegir el archivo correspondiente.
5. Configurar las credenciales necesarias en el entorno local.

Las credenciales y secretos no se incluyen en este repositorio.

## Seguridad

Este repositorio no contiene:

- API Keys;
- Client Secrets;
- tokens OAuth;
- contraseñas;
- archivos `.env`;
- credenciales personales.

Los workflows exportados requieren que cada usuario configure sus propias credenciales antes de ejecutarlos.
