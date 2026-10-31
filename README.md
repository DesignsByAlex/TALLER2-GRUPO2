# Taller: Ingeniería de prompts y de contexto

## Grupo 2

**Integrantes:**
- Daniel Andrade
- Camilo Gutierrez
- Alex Triana

## Caso seleccionado: CafeFET

CafeFET es un sistema ficticio de pedidos anticipados a la cafetería.

### Reglas de negocio

1. Se reciben pedidos de lunes a sábado, entre las 7:00 y las 18:00.
2. Cada pedido puede contener máximo 5 productos.
3. El pago se realiza con el saldo del carné estudiantil, sin permitir saldos negativos.
4. No se pueden solicitar productos agotados.
5. Los pedidos no recogidos en 30 minutos se cancelan y se reembolsa el saldo.

## Modelos utilizados

- `qwen3.5:4b` mediante `qwen-demo`.
- `phi4-mini` mediante `phi-demo`.
- `revisor-cafefet-v1` y `revisor-cafefet-v2`, creados mediante Modelfiles.

## Herramientas y entorno

- Windows 11
- Ollama
- PowerShell
- Visual Studio Code
- Python y uv para preparar el entorno del material docente

## Estructura del repositorio

- `reto1/`: prompt ambiguo, prompt mejorado, variante y comparación.
- `reto2/`: revisores especializados, código defectuoso y pruebas de ataques.
- `reto3/`: historia de usuario, criterios de aceptación y casos de prueba.
- `reto4/`: razonamiento y manejo del contexto.
- `practica_inicial/`: experimentos realizados antes de los retos oficiales.
- `base-docente/`: material de apoyo del docente.

## Reflexión del grupo

El taller permitió observar que un prompt ambiguo puede producir respuestas técnicamente elaboradas pero alejadas de las necesidades del proyecto. En el caso CafeFET, el modelo eligió inicialmente JavaScript y definió estructuras de datos sin conocer las reglas de negocio.

Al utilizar instrucciones organizadas, contexto explícito, delimitadores y restricciones, las respuestas se orientaron mejor hacia el problema. Sin embargo, también identificamos que una respuesta aparentemente completa puede contener errores lógicos u omisiones.

Los revisores especializados y las pruebas de inyección permiten analizar la importancia de separar las instrucciones del sistema de los datos proporcionados por el usuario. Las pruebas de contexto muestran que la posición y prioridad de las instrucciones pueden influir en el comportamiento del modelo.

Concluimos que la ingeniería de prompts y de contexto requiere experimentar, comparar resultados y verificar las respuestas, en lugar de confiar únicamente en el código generado.
