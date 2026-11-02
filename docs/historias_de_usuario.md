# Historias de usuario – MilaZen-Gestion

| N.º | Historia de usuario |
|---|---|
| 1 | Como usuario de MilaZen-Gestion, quiero registrar una venta con cliente, productos, medio de pago y monto abonado, para controlar lo vendido y lo que me deben en menos de 1 minuto. |
| 2 | Como usuario de MilaZen-Gestion, quiero que el stock se actualice solo con cada producción y cada venta y recibir alertas, para decidir qué producir primero. |
| 3 | Como usuario de MilaZen-Gestion, quiero cambiar precios y recetas con vigencia desde la fecha del cambio, para calcular la rentabilidad real sin alterar resultados anteriores. |

El seguimiento de estas historias (Ready, In progres, Done) está en el tablero del proyecto: https://github.com/users/rok3nrL/projects/1/views/1

## Criterios de aceptación
 
**Historia 1 – Registrar una venta**
- Se puede elegir un cliente registrado o dar de alta uno nuevo durante la carga del pedido.
- Se pueden cargar varios productos con sus cantidades, y el sistema calcula el total con los precios vigentes.
- Si no hay stock suficiente, el sistema lo advierte antes de confirmar la venta.
- Se registra el medio de pago y el monto abonado; si el pago es parcial, el saldo del cliente se actualiza con la diferencia.
- Una venta habitual se registra en 60 segundos o menos (promedio de 5 ventas de prueba).


**Historia 2 – Actualizar el stock y recibir alertas**
- Al confirmar una venta, el stock de cada producto baja según la cantidad vendida.
- Al registrar una producción, el stock del producto sube según la cantidad producida.
- Si el stock queda por debajo del mínimo establecido, el sistema genera una alerta de producción.


**Historia 3 – Cambiar precios y recetas con vigencia**
- Cada cambio de precio o de receta se guarda como una versión nueva con su fecha de vigencia (`fecha_desde`).
- El cambio rige desde esa fecha y no modifica ventas ni reportes anteriores.
- El costo final de una receta se calcula con los costos vigentes de sus materias primas.
- El reporte de rentabilidad de un período usa los precios y costos vigentes en cada fecha.