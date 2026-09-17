# README — Doña Ríos: Agente Base con Gemini (Checkpoint 1)

Este repositorio contiene la configuración, documentación y archivos correspondientes al **Checkpoint 1** del desarrollo del agente conversacional inteligente para **Doña Ríos – Almacén Saludable** (Río Cuarto, Córdoba, Argentina), configurado utilizando **Google Gemini** como modelo de lenguaje subyacente.

El proyecto está diseñado bajo una arquitectura modular en **n8n**, implementando un enfoque de **Agente con Autonomía Probabilística (Tools Agent / ReAct)** preparado para escalar progresivamente en futuros módulos.

---

## 🏗️ 1. Arquitectura del Workflow

El flujo se divide conceptualmente en dos tipos de conexiones fundamentales:
1. **Conexión lineal/secuencial del workflow:** Desde el disparador de chat hasta el reporte de observabilidad final.
2. **Conexiones auxiliares del agente:** Subnodos conectados directamente a los puertos específicos del agente (modelo de lenguaje y herramientas de decisión autónoma).

```text
                    ┌─────────────────────┐
                    │    Chat Trigger     │
                    │  Entrada usuario    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      AI Agent       │
                    │    Tools Agent      │
                    │  (Max Iterations: 8)│
                    │  System Prompt      │
                    └───────┬─────┬───────┘
                            │     │
                  Chat Model│     │Tool
                            │     │
                            ▼     ▼
                   ┌──────────┐  ┌──────────────┐
                   │ Google   │  │ Google Sheets│
                   │ Gemini   │  │    Tool      │
                   │ Model    │  └──────────────┘
                   └──────────┘
                            │
                            ▼
                    ┌─────────────────────┐
                    │       Gmail         │
                    │ Reporte / Log       │
                    └─────────────────────┘
```

## 📋 2. Componentes y Configuración del Checkpoint
🧩 Nodos Principales
Chat Trigger (Chat Trigger - Consulta Cliente): Punto de entrada conversacional para simular interacciones de usuario en tiempo real.

AI Agent (AI Agent - Atención Doña Ríos): Configurado bajo el tipo Tools Agent, operando con un límite de Max Iterations = 8 como guardrail para evitar bucles infinitos de razonamiento.

Google Gemini Chat Model (gemini-1.5-pro): Conectado lateralmente como cerebro lingüístico del agente.

Google Sheets Tool: Conectado estrictamente al puerto Tools del agente, permitiendo que el modelo decida de manera probabilística cuándo registrar un lead comercial.

Gmail: Nodo secuencial final destinado a la observabilidad y envío de reportes de ejecución del workflow.

## 📄 3. Estructura de la Planilla (Google Sheets)
La herramienta interactúa con la planilla Doña Ríos - Leads utilizando las siguientes columnas:

Fecha

Nombre

Consulta

Necesidad

Tipo de alimentación (ej. keto, low carb, sin gluten)

Estado

## 🤖 4. System Message y Comportamiento del Agente
ROL: Asistente virtual de atención y calificación de consultas de Doña Ríos - Almacén Saludable (Río Cuarto, Córdoba, Argentina).

ÁMBITO: Atención comercial y general sobre productos de alimentación keto, low carb y sin gluten. Operación exclusiva como tienda online (sin local físico de atención al público ni fabricación propia).

OBJETIVO: Comprender necesidades del usuario, responder con precisión comercial y registrar oportunidades comerciales reales mediante Google Sheets.

REGLAS DE COMUNICACIÓN: Uso exclusivo de español formal y cordial, prohibición de lenguaje inclusivo artificial, prohibición absoluta de inventar precios, stock, propiedades nutricionales o diagnósticos médicos.

RESTRICCIONES DE ACCIÓN: No realiza compras en nombre del cliente, no confirma pedidos sin validación, no modifica precios ni dispara herramientas ante interacciones sin sustento comercial.

USO DE HERRAMIENTAS: Activación exclusiva bajo criterios de intención comercial identificable.

ESCALAMIENTO: Derivación obligatoria al equipo humano ante situaciones fuera de alcance, falta de datos críticos o decisiones complejas.

## 📂 5. Estructura del Repositorio
```text
/
├── checkpoint1_soledad_rios.json
└── README.md
```
