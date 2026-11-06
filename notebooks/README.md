# Notebooks — Agente Inteligente FTTH EP2

## Notebook principal

**EP2_Agente_FTTH_Con_Interfaz_Visual.ipynb**

Esta es la versión principal del Agente Inteligente FTTH para la Evaluación Parcial 2. Integra LangGraph para organizar el flujo de diagnóstico, Chroma para recuperar antecedentes, Gemini para generar orientación técnica y Gradio como interfaz visual.

Permite ingresar una incidencia FTTH y visualizar la respuesta del agente, los antecedentes recuperados, el plan de verificación y las advertencias asociadas a las mediciones OTDR.

Las versiones anteriores se conservan como respaldo del desarrollo y de las pruebas realizadas.

## Requisitos de ejecución

- Google Colab con acceso a Internet.
- Dependencias indicadas en `requirements.txt`, ubicado en la raíz del repositorio.
- Archivo Excel FTTH anonimizado, proporcionado por separado.
- Clave `GOOGLE_API_KEY` configurada en Secretos de Colab, con acceso habilitado al notebook.

## Modos de funcionamiento

**demo:** utiliza antecedentes ficticios y respuestas deterministas, sin consultas a Gemini.

**real:** utiliza Chroma, embeddings de Gemini y generación de orientación mediante Gemini. Requiere credenciales válidas y puede consumir cuota de API.

## Instrucciones generales

1. Abrir el notebook principal en Google Colab.
2. Seleccionar el modo de funcionamiento.
3. Ejecutar las secciones en orden, desde la configuración hasta la construcción del grafo.
4. En modo real, cargar previamente el Excel anonimizado.
5. Ejecutar las pruebas funcionales y revisar sus resultados.

El notebook conserva salidas de pruebas anteriores. La ejecución completa de la versión consolidada desde una sesión limpia aún requiere validación.

## Alcances

Los escenarios SIM-001, SIM-002 y SIM-005 son simulados. En las pruebas registradas del modo real se utilizaron servicios de IA y recuperación semántica reales, pero no mediciones obtenidas de una incidencia productiva.

La orientación técnica requiere revisión humana y no reemplaza el diagnóstico de los especialistas en terreno.

## Respaldo de desarrollo

El archivo `EP2_Agente_FTTH_revision_sin_salidas.ipynb` conserva el historial de desarrollo anterior y no constituye el punto de entrada recomendado para revisar la entrega.Esta carpeta contiene el notebook del Agente Inteligente FTTH desarrollado para la EP2.
