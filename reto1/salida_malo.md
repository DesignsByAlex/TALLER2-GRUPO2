Aqu├¡ tienes un ejemplo completo y funcional de c├│mo crear una funci├│n para gestionar pedidos. He utilizado **JavaScript** (que es el est├índar m├ís com├║n), pero la l├│gica se puede adaptar f├ícilmente a Python, C#, Java o cualquier otro lenguaje.

Este ejemplo incluye:
1.  La estructura de los datos (Producto, Cantidad, Precio).
2.  Validaci├│n b├ísica (evitar cantidades negativas).
3.  C├ílculo autom├ítico del total.
4.  Simulaci├│n de guardado en una "base de datos" (un array).

### Ejemplo en JavaScript

```javascript
// Estructura de datos inicial (simulando una base de datos)
let pedidos = [];

/**
 * Funci├│n para crear un nuevo pedido
 * @param {string} idPedido - Identificador ├║nico del pedido
 * @param {string} clienteNombre - Nombre del cliente
 * @param {Array} items - Array de objetos con producto, cantidad y precio unitario
 * @returns {Object} Objeto con el estado del pedido creado o un mensaje de error
 */
function crearPedido(idPedido, clienteNombre, items) {
    // 1. Validaciones b├ísicas
    if (!idPedido || !clienteNombre) {
        return { exito: false, mensaje: "Faltan datos obligatorios (ID y Cliente)." };
    }

    if (!Array.isArray(items) || items.length === 0) {
        return { exito: false, mensaje: "El pedido debe contener al menos un producto." };
    }

    // Validar que todos los items tengan precio y cantidad v├ílidos
    for (let i = 0; i < items.length; i++) {
        const item = items[i];
        if (!item.precio || !item.cantidad) {
            return { exito: false, mensaje: `El producto ${i} falta informaci├│n de precio o cantidad.` };
        }
        if (item.cantidad <= 0) {
            return { exito: false, mensaje: "La cantidad no puede ser menor a 1." };
        }
    }

    // 2. Calcular el total del pedido
    let total = 0;
    const itemsProcesados = [];

    for (let i = 0; i < items.length; i++) {
        const item = items[i];
        const subtotal = item.precio * item.cantidad;
        total += subtotal;
        
        itemsProcesados.push({
            ...item, // Copia del objeto original
            subtotal: subtotal,
            idProducto: item.id || `PROD-${i}` // Asignar ID si no existe
        });
    }

    // 3. Crear el objeto pedido completo
    const nuevoPedido = {
        id: idPedido,
        fecha: new Date().toISOString(), // Fecha actual en formato ISO
        cliente: clienteNombre,
        items: itemsProcesados,
        total: total.toFixed(2) // Formatear a 2 decimales
    };

    // 4. Guardar el pedido (simulaci├│n de persistencia)
    pedidos.push(nuevoPedido);

    return {
        exito: true,
        mensaje: `

