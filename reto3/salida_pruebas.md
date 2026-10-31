| Caso | Entrada | Resultado esperado | Criterio que cubre |
|------|---------|---------------------|--------------------|
| Repetición exitosa (con historial) | Usuario selecciona "Repetir pedido" tras haber realizado una compra anterior en el día. | Se genera un nuevo pedido idéntico al anterior, se actualiza el saldo y se confirma la compra. | Repetición de pedidos |
| Falta de historial | Usuario intenta repetir pedido sin haber realizado ninguna compra en el día. | El sistema muestra un mensaje indicando que no hay pedidos previos para repetir y ofrece opciones de compra desde cero. | Falta de historial |
| Horario inválido (fuera de horario) | Usuario intenta realizar una acción o ver productos fuera del rango 07:00–18:00. | El sistema bloquea la acción y muestra un mensaje indicando que el servicio no está disponible en ese momento. | Horario de operación |
| Saldo insuficiente | Usuario intenta añadir un producto cuyo precio supera su saldo actual en el carné. | El sistema impide la compra, muestra el saldo disponible y sugiere completar el pago o retirar más fondos. | Saldo del carné nunca negativo |
| Producto agotado | Usuario selecciona un producto que aparece como "Agotado" en el catálogo. | El sistema bloquea la selección y muestra un mensaje indicando que el producto no está disponible. | No incluir productos agotados |
| Límite de productos excedido | Usuario intenta añadir el sexto producto a su carrito (ya tiene 5). | El sistema impide la adición y muestra un mensaje recordando el límite máximo de 5 productos por pedido. | Máximo 5 productos |

**Verificación de cobertura:**
- ✅ Repetición exitosa: Cubierto (Caso 1)
- ✅ Falta de historial: Cubierto (Caso 2)
- ✅ Horario inválido: Cubierto (Caso 3)
- ✅ Saldo insuficiente: Cubierto (Caso 4)
- ✅ Producto agotado: Cubierto (Caso 5)
- ✅ Máximo de productos: Cubierto (Caso 6)

Todos los criterios requeridos están cubiertos por al menos un caso. No se han agregado casos adicionales ni se han inventado reglas nuevas.

