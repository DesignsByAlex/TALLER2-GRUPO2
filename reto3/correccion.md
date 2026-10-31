# Reto 3 — Corrección y comparación de resultados

## Requisito nuevo

Como estudiante, quiero repetir mi último pedido con un solo clic, para ahorrar tiempo al realizar una nueva compra.

## Primera ejecución

Se generó una historia de usuario, cuatro criterios de aceptación y una tabla de casos de prueba.

### Primeras deficiencias observadas

En los criterios de aceptación no apareció un criterio específico que comprobara directamente la acción de repetir el último pedido con un clic.

En la tabla de pruebas original, el modelo introdujo la condición de que la compra anterior debía haberse realizado "en el día". Esta restricción no forma parte de las reglas oficiales de CafeFET.

Además, inventó comportamientos no definidos para estudiantes sin historial, como mostrar opciones de compra desde cero.

La verificación de cobertura original afirmó que todos los criterios estaban cubiertos, pero utilizó nombres generales en vez de relacionar los casos con los cuatro criterios CA-01 a CA-04. Por tanto, la cobertura no quedó demostrada correctamente.

## Corrección aplicada

Se creó `prompt_pruebas_corregido.txt`, que:

1. Reitera las cinco reglas de CafeFET.
2. Exige validar nuevamente las reglas al repetir el pedido.
3. Prohíbe inventar restricciones adicionales.
4. Solicita identificar comportamientos no especificados.
5. Exige verificar la cobertura de los criterios.

La ejecución corregida se guardó en `salida_pruebas_corregida.md`.

## Comparación

| Aspecto | Primera ejecución | Ejecución corregida |
|---|---|---|
| Pedido anterior | Introdujo la restricción inventada "en el día". | No exige que el pedido anterior sea del mismo día. |
| Sin historial | Inventó un mensaje y opciones de compra. | Reconoce que el comportamiento está pendiente de definir. |
| Identificación de casos | Utilizó nombres descriptivos sin vinculación clara con CA-01 a CA-04. | Utilizó identificadores C1 a C6. |
| Revalidación | No quedó explícita de forma consistente. | Incluyó una nota para volver a validar horario, cantidad, saldo y disponibilidad. |
| Regla de 30 minutos | No presentó un caso específico. | Tampoco presentó un caso específico. |

## Limitaciones de la respuesta corregida

La segunda respuesta todavía tiene problemas:

- El caso C5 habla de repetir un pedido realizado fuera de horario, cuando la validación debería centrarse en la fecha y hora actuales del nuevo pedido.
- No incluye una prueba específica de cancelación y reembolso después de 30 minutos.
- Los identificadores C1 a C6 son categorías creadas por la segunda respuesta, no una trazabilidad exacta con los criterios originales CA-01 a CA-04.
- El caso exitoso debería confirmar explícitamente la creación de un nuevo pedido con un clic, después de superar todas las validaciones.

## Conclusión

La corrección redujo la invención de reglas y mejoró la identificación de información no especificada. Sin embargo, no resolvió todos los problemas de cobertura y trazabilidad.

El ejercicio demuestra que la ingeniería de prompts es iterativa: mejorar las instrucciones ayuda, pero sigue siendo necesario revisar los resultados frente a los requisitos originales.

