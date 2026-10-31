# Reto 4 — Razonamiento y manejo del contexto

## Parte A. Comparación del razonamiento

Se utilizó `phi-demo` para analizar una función defectuosa de CafeFET mediante dos prompts: uno solicitando una explicación breve y otro solicitando la evaluación de cada condición.

El caso utilizado contenía seis productos de 2.000 cada uno, un saldo de 11.000 y una hora de pedido de las 10:00.

La función devuelve `True`, porque `6 > 6` es falso, `-1000 < -1000` también es falso y la condición del horario es verdadera.

Sin embargo, el pedido debería rechazarse porque supera el máximo de cinco productos y dejaría el saldo negativo.

**Resultado del prompt corto:** [Escribir qué respondió realmente el modelo y si identificó los dos errores].

**Resultado del prompt paso a paso:** [Escribir qué respondió realmente el modelo y si evaluó correctamente las tres condiciones].

**Comparación:** [Indicar cuál tuvo menos errores y por qué].

## Parte B. Manejo del contexto

Se configuró `num_ctx 512` para limitar la ventana de contexto de `qwen-demo`.

En la primera prueba se indicó una regla de formato mediante un mensaje normal del usuario y posteriormente se enviaron dos mensajes extensos.

**Resultado de la regla como usuario:** [Indicar si la respuesta final comenzó con CAFEFET y terminó con FIN].

En la segunda prueba se limpió la conversación mediante `/clear` y se estableció la regla utilizando `/set system`.

**Resultado de la regla como sistema:** [Indicar si la respuesta final comenzó con CAFEFET y terminó con FIN].

**Conclusión:** Una ventana de contexto pequeña puede provocar que se pierdan mensajes antiguos al incorporarse información nueva. Las instrucciones de sistema tienen una prioridad distinta de los mensajes normales y pueden mantenerse disponibles de otra manera, pero la prueba debe interpretarse según el comportamiento realmente observado.