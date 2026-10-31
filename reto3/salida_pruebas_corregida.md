| Caso | Entrada | Resultado esperado | Criterio que cubre |
| :--- | :--- | :--- | :--- |
| **C1** | El usuario selecciona "Repetir pedido" para un pedido válido realizado anteriormente dentro del horario de atención. | Se muestra el resumen del último pedido con los productos disponibles y se permite añadirlos al carrito. | C1: Repetición exitosa |
| **C2** | El usuario intenta añadir 6 productos a su pedido repetido (excediendo el límite). | El sistema bloquea la acción y muestra un mensaje indicando que el máximo permitido es de 5 productos. | C2: Pedido con más de 5 productos |
| **C3** | El usuario intenta realizar una compra con un saldo en el carné inferior al coste total del pedido repetido. | El sistema bloquea la transacción, mantiene el saldo actual y muestra un mensaje de "Saldo insuficiente". | C3: Saldo insuficiente |
| **C4** | El usuario selecciona productos que aparecen como agotados en su último pedido (o en tiempo real). | El sistema no permite añadir esos productos específicos al nuevo pedido, mostrando un mensaje de "Producto agotado". | C4: Producto agotado |
| **C5** | El usuario intenta repetir un pedido realizado fuera del horario de atención (antes de las 07:00 o después de las 18:00). | El sistema muestra un mensaje indicando que el servicio no está disponible en ese momento y bloquea la repetición. | C5: Pedido fuera de horario |
| **C6** | El usuario accede a la opción de "Repetir pedido" sin tener ningún historial de compras previo registrado. | **Acción requerida:** Debe definirse el comportamiento (ej. mostrar mensaje de error, redirigir al inicio o permitir compra desde cero). Actualmente no se especifica qué ocurre. | C6: Estudiante sin pedido anterior |

### Notas del Analista:
1.  **Validación de Reglas:** En los casos C1 a C5, el sistema debe ejecutar una validación completa antes de confirmar la repetición, verificando nuevamente las reglas de horario (C5), límite de productos (C2), saldo (C3) y disponibilidad (C4).
2.  **Definición Pendiente:** El caso **C6** destaca que falta información sobre el comportamiento por defecto cuando no existe un pedido previo. Se recomienda definir si la opción "Repetir" debe estar oculta, mostrar un mensaje de error explícito o si se debe interpretar como una compra nueva desde cero.
3.  **Tiempo de Espera:** Aunque la regla 5 menciona la cancelación por inactividad de 30 minutos, no se ha incluido un caso específico para "Pedido repetido después de 30 minutos sin actividad", ya que el sistema debería cancelar automáticamente antes de permitir la repetición o mostrar al usuario que su pedido expiró.

