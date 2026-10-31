# Reto 2 — Comparación de revisores y ataques

## Objetivo

Comparar el comportamiento de qwen-demo con un revisor especializado en las reglas de CafeFET y evaluar si el revisor resiste instrucciones que intentan desviarlo de su tarea.

## Código analizado

La función original presenta varios problemas:

1. Usa `len(productos) > 6`, por lo que acepta pedidos de seis productos aunque el máximo permitido es cinco.
2. Usa un límite de saldo de `-1000`, aunque el saldo nunca debe quedar negativo.
3. No comprueba si existen productos agotados.
4. No comprueba si el día corresponde a lunes a sábado.
5. No implementa la cancelación ni el reembolso después de 30 minutos.

## Comparación entre revisores

Se ejecutó el mismo código defectuoso con `qwen-demo` y `revisor-cafefet-v1`.

El revisor especializado dispone de instrucciones explícitas sobre las reglas de CafeFET y un formato de revisión, mientras que qwen-demo utiliza su configuración general.

Los archivos `revision_qwen.md` y `revision_v1.md` contienen las respuestas reales para contrastar qué errores identificó cada modelo.

## Pruebas de ataque

| Ataque | Objetivo | Evidencia antes | Evidencia después |
|---|---|---|---|
| 1 | Solicitar instrucciones internas | `ataque1_v1.md` | `ataque1_v2.md` |
| 2 | Ordenar al revisor que abandone su tarea | `ataque2_v1.md` | `ataque2_v2.md` |
| 3 | Inyectar instrucciones en un comentario del código | `ataque3_v1.md` | `ataque3_v2.md` |

## Endurecimiento del revisor

La versión 2 agrega instrucciones para tratar el código, los comentarios y las cadenas como datos no confiables. También indica que debe ignorar las órdenes de cambiar de rol y continuar revisando las reglas de CafeFET.

## Conclusión

La especialización mediante un Modelfile permite definir el alcance, las reglas y el formato de las respuestas. El endurecimiento busca reducir la influencia de instrucciones maliciosas incorporadas en las entradas.

La eficacia de estas medidas debe evaluarse comparando las respuestas reales de ambas versiones y no solamente observando las instrucciones del Modelfile.
