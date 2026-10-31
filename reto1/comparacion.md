# Reto 1 — Comparación de prompts

## 1. Prompt malo

Prompt utilizado: "Haz una función para crear pedidos."

El prompt no especifica el lenguaje de programación, el contexto de CafeFET, las reglas de negocio, la estructura de datos ni el formato de respuesta.

## 2. Cinco decisiones que el modelo tuvo que adivinar

1. Lenguaje de programación: seleccionó JavaScript.
2. Estructura del pedido: definió identificadores, clientes y productos.
3. Almacenamiento: utilizó un arreglo para simular persistencia.
4. Validaciones: estableció sus propias comprobaciones de datos.
5. Cálculo y pago: decidió cómo calcular el total sin conocer el sistema de saldo del carné.

## 3. Prompt mejorado

Se utilizó una estructura de cinco bloques:
- Qué quiero.
- Para quién.
- Contexto.
- Formato de salida.
- Restricciones.

Las cinco reglas de CafeFET se incluyeron dentro de etiquetas <reglas>.

En la respuesta observada, el modelo utilizó Python, incorporó validaciones de cantidad e inventario y empezó a considerar el saldo del carné.

## 4. Variante

Se mantuvo el prompt mejorado y se eliminó únicamente el bloque RESTRICCIONES.

Esta modificación permite estudiar la influencia de las restricciones explícitas sin cambiar el contexto ni el formato solicitado.

## 5. Análisis

El prompt malo dio libertad al modelo para inventar decisiones técnicas. El prompt mejorado proporcionó reglas de negocio y un formato definido.

Sin embargo, una respuesta más estructurada no garantiza que la implementación sea correcta. Es necesario comprobar el saldo después del pago, el horario, el inventario, el límite de productos y la cancelación con reembolso.

## 6. Conclusión

La precisión del prompt ayuda a orientar la respuesta hacia los requisitos de CafeFET. Los resultados generados deben revisarse porque pueden contener omisiones o errores de lógica.
