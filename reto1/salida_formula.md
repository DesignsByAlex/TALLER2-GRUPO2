Aqu├¡ tienes la implementaci├│n de la funci├│n `crear_pedido` en Python, dise├▒ada estrictamente bajo las reglas de negocio de CafeFET.

### C├│digo Python

```python
from datetime import datetime, timedelta
from typing import List, Dict, Optional

# Simulaci├│n de estado del sistema (en un caso real, esto vendr├¡a de una base de datos)
INVENTARIO = {
    "cafe_latte": {"stock": 10, "precio": 2.5},
    "croissant": {"stock": 8, "precio": 1.5},
    "tarta_chocolate": {"stock": 3, "precio": 3.0}
}

# Simulaci├│n de saldo del carn├® (en un caso real, esto vendr├¡a de la base de datos)
SALDO_CARNE = 20.0

def crear_pedido(
    productos: List[str], 
    cantidad: int, 
    saldo_actual: float, 
    hora_recogida_estimada: Optional[datetime] = None
) -> Dict:
    """
    Crea un pedido anticipado en CafeFET validando las reglas de negocio.

    PAR├üMETROS:
        - productos (List[str]): Lista de nombres de productos a pedir.
        - cantidad (int): Cantidad total de productos (se valida que sea <= 5).
        - saldo_actual (float): Saldo disponible en el carn├® del estudiante.
        - hora_recogida_estimada (Optional[datetime]): Hora estimada de recogida (opcional para l├│gica futura).

    VALOR DE RETORNO:
        - Un diccionario con el estado del pedido:
            * 'exito' (bool): ┬┐Se cre├│ el pedido?
            * 'mensaje' (str): Mensaje descriptivo.
            * 'saldo_final' (float): Saldo restante tras la transacci├│n.
            * 'productos_agotados' (List[str]): Lista de productos que no se pudieron incluir.
    """

    global SALDO_CARNE, INVENTARIO

    # Regla 1: Validaci├│n b├ísica de cantidad (m├íximo 5 productos)
    if cantidad > 5:
        return {
            'exito': False, 
            'mensaje': f"Error: Se permite un m├íximo de 5 productos por pedido. Solicitaste {cantidad}.",
            'saldo_final': SALDO_CARNE,
            'productos_agotados': []
        }

    # Regla 3: Validaci├│n de saldo (nunca negativo)
    if saldo_actual < 0:
        return {
            'exito': False, 
            'mensaje': "Error: El saldo del carn├® no puede ser negativo.",
            'saldo_final': SALDO_CARNE,
            'productos_agotados': []
        }

    # Regla 4: Validaci├│n de inventario y c├ílculo de costo
    productos_validos = []
    costo_total = 0.0
    productos_agotados = []

    for prod in productos:
        if prod not in INVENTARIO:
            return {
                'exito': False, 
                'mensaje': f"Error

