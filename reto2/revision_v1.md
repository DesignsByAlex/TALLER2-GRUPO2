# Análisis de Código Python para CafeFET

## Hallazgos, Regla afectada, Caso límite, Corrección propuesta

### 1. Límite de productos incorrecto
- **Regla afectada**: Máximo 5 productos por pedido.
- **Caso límite**: El código verifica `len(productos) > 6`, permitiendo hasta 6 productos en lugar del máximo permitido (5).
- **Corrección propuesta**: Cambiar la condición a `if len(productos) > 5:` para cumplir con el límite de 5 productos.

### 2. Validación de saldo incorrecta
- **Regla afectada**: Saldo nunca negativo.
- **Caso límite**: La condición `est.saldo - sum(p.precio for p in productos) < -1000` permite transacciones donde el saldo resultante sea menor a -1000, lo cual viola la regla de que el saldo nunca debe ser negativo. Además, no valida si el saldo es exactamente 0 o negativo después de la compra.
- **Corrección propuesta**: Cambiar la condición a `if est.saldo < sum(p.precio for p in productos):` para asegurar que el saldo restante sea siempre mayor o igual a cero.

### 3. Validación de horario incompleta
- **Regla afectada**: Lunes a sábado de 7:00 a 18:00.
- **Caso límite**: El código verifica solo `7 <= hora <= 18`, pero no considera el día de la semana. Si se realiza un pedido en domingo o festivo, la validación fallará.
- **Corrección propuesta**: Agregar una validación del día de la semana: `if not (7 <= hora <= 18 and est.dia_semana in ['lunes', 'martes', 'miércoles', 'jueves', 'viernes', 'sábado']):`.

### 4. Validación de productos agotados ausente
- **Regla afectada**: Productos agotados no permitidos.
- **Caso límite**: No hay ninguna verificación para asegurar que los productos seleccionados estén disponibles (no agotados).
- **Corrección propuesta**: Agregar una validación iterando sobre los productos: `if any(p.agotado for p in productos): return False`.

### 5. Validación de cancelación con reembolso ausente
- **Regla afectada**: Cancelación con reembolso después de 30 minutos.
- **Caso límite**: No se verifica el tiempo transcurrido desde la creación del pedido para permitir o denegar reembolsos.
- **Corrección propuesta**: Agregar una validación basada en el tiempo: `if (hora_actual - hora_pedido) < 30 minutos: return False` (asumiendo que se requiere más de 30 minutos para cancelar con reembolso).

### Información faltante
- No se proporciona información sobre cómo se determina el día de la semana (`est.dia_semana`).
- No se especifica cómo se calcula el tiempo transcurrido desde la creación del pedido.
- No se indica si hay otros campos en `est` o `productos` que podrían ser relevantes para estas validaciones.

