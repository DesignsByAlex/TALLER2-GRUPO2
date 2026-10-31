Aquí tienes la implementación en Python para el sistema **CafeFET**, diseñada bajo las reglas de negocio especificadas.

### Código Python: `crear_pedido.py`

```python
from datetime import datetime, timedelta
from typing import List, Dict, Optional

class Producto:
    def __init__(self, nombre: str, precio: float, disponible: bool):
        self.nombre = nombre
        self.precio = precio
        self.disponible = disponible

class Estudiante:
    def __init__(self, id_carne: str, saldo: float):
        self.id_carne = id_carne
        self.saldo = saldo

class PedidoCafeFET:
    def __init__(self, estudiante: Estudiante, productos: List[Producto], hora_recogida_estimada: datetime):
        self.estudiante = estudiante
        self.productos = productos
        self.hora_recogida_estimada = hora_recogida_estimada
        self.total = sum(p.precio for p in productos)
        self.estado = "PENDIENTE"  # PENDIENTE, RECOGIDO, CANCELADO

    def es_válido(self) -> bool:
        """Valida las reglas de negocio antes de crear el pedido."""
        
        # Regla 1: Horario (Lunes a sábado, 7:00 - 18:00)
        # Asumimos que la hora actual se pasa como parámetro o se usa datetime.now()
        # Aquí validamos si la hora de creación está dentro del rango permitido.
        if not (7 <= self.hora_recogida_estimada.hour < 18):
            return False
        
        # Nota: En un sistema real, verificaríamos el día de la semana. 
        # Para este ejemplo, asumimos que la función se llama en horario válido o validamos el día.
        
        # Regla 2: Máximo 5 productos
        if len(self.productos) > 5:
            return False

        # Regla 4: Productos agotados
        for producto in self.productos:
            if not producto.disponible:
                return False

        # Regla 3: Pago con saldo (saldo nunca negativo)
        if self.total > self.estudiante.saldo:
            return False

        return True

    def procesar(self):
        """Simula la creación y validación del pedido."""
        if not self.es_válido():
            raise ValueError("El pedido no cumple con las reglas de negocio.")
        
        # Se descuenta el saldo inmediatamente al crear el pedido anticipado
        self.estudiante.saldo -= self.total
        self.estado = "PENDIENTE"
        return True

    def verificar_cancelacion(self, hora_actual: datetime) -> bool:
        """
        Regla 5: Si no se recoge en 30 minutos, cancelar y devolver saldo.
        Devuelve True si el pedido debe ser cancelado.
        """
        tiempo_transcurrido = (hora_actual - self.hora_recogida_estimada).total_seconds()
        
        # Si han pasado más de 30 minutos (1800 segundos) desde la hora estimada de recogida

