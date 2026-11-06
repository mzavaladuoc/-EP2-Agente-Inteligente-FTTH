# EP2 – Agente Inteligente para Diagnóstico FTTH

**Ingeniería de Soluciones con Inteligencia Artificial – Duoc UC**

## 1. Descripción del proyecto

Este proyecto corresponde a la Evaluación Parcial 2 (EP2) y representa la continuación del trabajo realizado en la EP1, donde se desarrolló un sistema RAG para apoyar el diagnóstico de incidencias en redes de fibra óptica FTTH.

En esta segunda etapa se incorpora un agente inteligente basado en LangGraph, capaz de organizar un flujo de diagnóstico, consultar antecedentes técnicos, generar un plan de revisión y entregar una orientación mediante Gemini.

La solución busca apoyar el trabajo de supervisión y diagnóstico en terreno, sin reemplazar las mediciones, la validación técnica ni las decisiones del personal especializado.

## 2. Objetivo

Desarrollar un prototipo de agente inteligente que permita analizar incidencias FTTH utilizando antecedentes históricos, planificación de verificaciones, contexto de mediciones OTDR y mecanismos de conservación del estado de cada incidencia.

## 3. Tecnologías utilizadas

| Tecnología | Función |
|---|---|
| Python y Google Colab | Desarrollo y ejecución del prototipo |
| LangGraph | Organización del flujo de trabajo del agente |
| LangChain | Integración de componentes de IA y recuperación |
| Google Gemini | Generación de orientación técnica |
| Chroma | Almacenamiento y búsqueda vectorial |
| RAG | Recuperación de antecedentes relevantes |
| JSON y Google Drive | Respaldo y recuperación de estados |
| Matplotlib | Visualización de mediciones OTDR |
| GitHub | Control de versiones y documentación |

## 4. Arquitectura del agente
[Ver arquitectura y diagrama de orquestación](docs/ARQUITECTURA.md)

El flujo principal implementado en LangGraph V8 es:

1. **Supervisor:** recibe la incidencia y comprueba si existe información suficiente para continuar.
2. **Consulta RAG:** recupera antecedentes relacionados desde la base vectorial.
3. **Planificación:** genera una secuencia de verificaciones técnicas según el contexto disponible.
4. **Orientación técnica:** utiliza Gemini para elaborar recomendaciones considerando antecedentes, planificación y mediciones.
5. **Validación OTDR:** incorpora una advertencia cuando existen mediciones desde diferentes puntos de origen.

El prototipo combina reglas programadas con generación de lenguaje mediante un modelo de IA. La selección de herramientas y el recorrido del grafo están definidos principalmente por el código.

## 5. Funcionalidades desarrolladas

- Consulta de antecedentes FTTH mediante RAG.
- Clasificación inicial de información faltante.
- Planificación de verificaciones técnicas.
- Incorporación de distancia OTDR actual.
- Registro de múltiples mediciones históricas.
- Identificación de mediciones realizadas desde diferentes orígenes.
- Generación de orientación técnica mediante Gemini.
- Conservación temporal del estado mediante `InMemorySaver`.
- Exportación y recuperación de estados mediante archivos JSON en Google Drive.
- Restauración de un estado recuperado en una sesión independiente de LangGraph.

## 6. Prueba de integración SIM-005

Se desarrolló una prueba simulada correspondiente a clientes FTTH sin servicio, con posible daño físico en una caja CTO.

**Resultados obtenidos:**

| Elemento | Resultado |
|---|---|
| Ticket | SIM-005 |
| Antecedentes RAG | 3 |
| Verificaciones planificadas | 6 |
| Primera medición OTDR | 850 m desde mufa simulada |
| Segunda medición OTDR | 1.250 m desde nodo simulado |
| Validación de orígenes | Diferentes |
| Recuperación del estado | Superada |

Las dist

## Interfaz visual del Agente FTTH

El prototipo incorpora una interfaz desarrollada con Gradio que permite ingresar incidencias FTTH y visualizar la orientación generada, los antecedentes recuperados, el plan de verificación y las advertencias asociadas a mediciones OTDR.

- [Notebook principal con interfaz Gradio](notebooks/EP2_Agente_FTTH_Con_Interfaz_Visual.ipynb)
- [Documentación de la interfaz](docs/INTERFAZ_GRADIO.md)
- [Evidencia visual SIM-005](evidencias/EP2_Gradio_SIM005_Evidencia.png)

La aplicación se ejecuta desde Google Colab. El modo real requiere credenciales de Gemini y una base FTTH anonimizada. El enlace temporal de Gradio solo permanece disponible mientras la sesión correspondiente esté activa.
