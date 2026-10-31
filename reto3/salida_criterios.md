Como analista de requisitos de CafeFET, basándome en la historia de usuario y las reglas proporcionadas, aquí tienes 4 criterios de aceptación diseñados para cubrir tanto los flujos de éxito como los casos de rechazo, asegurando que se respeten todas las restricciones del sistema:

**CA-01: Validación de productos disponibles y cantidad máxima**
*   **Dado** que el usuario intenta añadir productos a su pedido repetido.
*   **Cuando** el sistema verifica la disponibilidad de stock y la cantidad total solicitada.
*   **Entonces**:
    *   Si hay productos agotados o la suma supera los 5 artículos, se muestra un mensaje de error indicando qué productos no están disponibles o cuántos exceden el límite.
    *   Si todos los productos están disponibles y la cantidad es válida, se permite añadirlos al carrito.

**CA-02: Verificación del saldo antes de confirmar pedido**
*   **Dado** que el usuario ha seleccionado sus productos y está a punto de finalizar el pedido.
*   **Cuando** el sistema calcula el total a pagar contra el saldo actual del carné.
*   **Entonces**:
    *   Si el saldo es suficiente para cubrir el total, se procede a la confirmación del pedido.
    *   Si el saldo es insuficiente (el saldo resultante sería negativo), se bloquea la confirmación y se notifica al usuario que debe completar su saldo antes de poder realizar la compra.

**CA-03: Validación de horario de atención**
*   **Dado** que el usuario intenta iniciar o confirmar un pedido repetido.
*   **Cuando** el sistema verifica la hora actual contra el horario de operación (Lunes a sábado, 7:00 - 18:00).
*   **Entonces**:
    *   Si está dentro del horario de atención, se permite la ejecución del pedido.
    *   Si está fuera del horario (antes de las 7:00 o después de las 18:00), se bloquea la acción y se informa al usuario que el servicio no está disponible en ese momento.

**CA-04: Gestión del tiempo de espera y cancelación automática**
*   **Dado** que un pedido ha sido confirmado y enviado a preparación.
*   **Cuando** transcurridos 30 minutos desde la confirmación sin que el usuario haya recogido el pedido.
*   **Entonces**:
    *   El sistema cancela automáticamente el pedido en curso.
    *   Se libera los productos reservados y se devuelve el saldo del carné al estado original, registrando el motivo de cancelación por tiempo de espera.

