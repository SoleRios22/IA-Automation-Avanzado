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
