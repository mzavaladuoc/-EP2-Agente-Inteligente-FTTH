# Interfaz Gradio — EP2 Agente Inteligente FTTH

La interfaz visual es una capa de demostración conectada al agente implementado con LangGraph. Permite ingresar incidencias simuladas, consultar Chroma en modo `real`, mostrar el plan técnico, consultar Gemini y observar las advertencias OTDR.

## Cómo ejecutar

1. Abrir `notebooks/EP2_Agente_FTTH_Con_Interfaz_Visual.ipynb` en Google Colab.
2. Configurar `GOOGLE_API_KEY` en **Secretos de Colab** sin incluir la clave en el código.
3. Para modo `real`, cargar **por separado** el Excel FTTH anonimizado y ejecutar en orden las secciones 1 a 5.
4. Ejecutar la sección 10 (interfaz Gradio). Se solicita una contraseña temporal de 8 caracteres o más y se crea un enlace temporal de Gradio.
5. Abrir el enlace, iniciar sesión como `supervisor` con la contraseña temporal configurada, seleccionar el ejemplo SIM-005 y pulsar **Analizar incidencia**.
6. Revisar los paneles de respuesta, ruta, antecedentes RAG, planificación y validación OTDR.

Para probar una incidencia diferente, modificar la descripción y **desmarcar** las mediciones OTDR simuladas de SIM-005. Cada consulta crea un ticket independiente; el panel de chat no constituye una memoria conversacional persistente.

## Consideraciones

- Los escenarios SIM-001, SIM-002 y SIM-005 y las mediciones OTDR son **simulados**. En modo `real`, Chroma y Gemini se ejecutan efectivamente.
- La selección de nodos se realiza mediante reglas programadas, no por un razonamiento interno observable del LLM.
- `InMemorySaver` conserva estados **durante la sesión**; el JSON en modo real es un resumen, no una base persistente de checkpoints.
- La interfaz Gradio crea una URL **temporal**, que no reemplaza el notebook ni el repositorio para la entrega.
- La API puede generar costos o consumir cuota. No subir secretos, Excel original ni información de clientes al repositorio.
- Se han probado interacciones mediante Gradio; la ejecución completa desde una sesión limpia todavía requiere validación.

**Repositorio:** https://github.com/mzavaladuoc/-EP2-Agente-Inteligente-FTTH
