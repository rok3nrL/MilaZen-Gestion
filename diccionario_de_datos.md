## Tabla Productos

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_producto | Integer | 8 | PK | Identificación numérica única del producto para el programa |
| nombre | String | 50 | Obligatorio | Nombre comercial, para facilitar su búsqueda y reconocimiento dentro del programa |
| categoria | String | 20 | Milanesas / Empanadas | División en categorías, facilita la visualización de ventas por separado |
| precio_revendedor | Float | 8 | Mayor que 0 | Precio de venta que no aplica retroactivo cuando se modifica, para revendedores |
| precio_consumidor_f | Float | 8 | Mayor que 0 | Precio de venta que no aplica retroactivo cuando se modifica, para consumidor final |
| stock | Integer | 8 | Mayor o igual que 0 | Contabilización de unidades disponibles, sube con producción, baja con ventas |
| costo | Float | 8 | Mayor o igual que 0 | Costo de producción, necesario para calcular rentabilidad |
| unidad_x_bulto | Integer | 8 | Mayor que 0 | Unidades que contiene cada paquete, util para calcular costos y rentabilidad |
| codigo_barra | String | 13 | Único | Código de barra único para identificar producto con lectora. |

## Tabla Materia Prima

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_materia_prima | Integer | 8 | PK | Identificación numérica única de la materia prima para el programa |
| nombre | String | 20 | Obligatorio / Único | Nombre, para facilitar su búsqueda y reconocimiento dentro del programa |
| id_proveedor | Integer | 8 | FK a proveedor, opcional | Proveedor, facilita el seguimiento de deuda y pagos |
| precio_costo | Float | 8 | Mayor a 0 | Precio de costo que aplica el dia de la modificación, no afecta reportes anteriores |
| stock | Float | 8 | Mayor o igual que 0 | Contabilización de unidades disponibles, sube con compra, baja con producción |
| unidad_medida | String | 8 | Kg o unidad | Unidad en que se va a medir y descontar de manera adecuada al producir o adquirir. |
| unidad_x_bulto | Float | 8 | Mayor que 0 | Cantidad de unidades o peso del bulto de materia prima. |

## Tabla Recetas

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_receta | Integer | 8 | PK | Identificación numérica única de la receta para el programa |
| id_producto | Integer | 8 | FK a Productos | Producto elaborado |
| id_materia_prima | Integer | 8 | FK a Materia Prima | Ingrediente |
| cantidad | Float | 8 | Mayor a 0 / unidad o KG | Cantidad por unidad o KG. |

## Tabla Proveedor

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_proveedor | Integer | 8 | PK | Identificación numérica única del proveedor para el programa |
| nombre | String | 30 | Obligatorio / Único | Razón social o nombre |
| numero_telefonico | String | 20 | Solo dígitos | Contacto telefónico |
| saldo | Float | 8 | Mayor o igual a 0 | Deuda pendiente con el proveedor |

## Tabla Clientes

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_cliente | Integer | 8 | PK | Identificación numérica única del cliente para el programa |
| nombre | String | 20 | Obligatorio | Nombre, para facilitar su búsqueda y reconocimiento dentro del programa |
| categoria | String | 20 | Revendedor / Consumidor final | División en categorías, facilita que lista de precio usar |
| numero_telefonico | String | 20 | Solo dígitos | Número para facilitar el contacto |
| saldo | Float | 8 | Mayor o igual que 0 | Saldo calculado entre lo comprado y pagado por el cliente |

## Tabla Ventas

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_venta | Integer | 8 | PK | Identificación numérica única de la venta para el programa |
| id_cliente | Integer | 8 | FK a clientes | Cliente al que se relaciona la venta |
| fecha | Date | - | formato dd/mm/aaaa | Fecha de la venta realizada |
| medio_pago | String | 20 | Efectivo / Transferencia | Forma de abonar del cliente |
| total | Float | 8 | Mayor o igual que 0 | Total de la venta a abonar (Suma de los subtotales de los renglones de la venta) |
| pago | Boolean | - | True / False | True -> se descuenta el total. False -> se utiliza monto pagado o cliente adeuda el total |
| monto_pagado | Float | 8 | Mayor o igual que 0 | En caso de no abonar el total, sirve para descontar del total |
| observaciones | String | 200 | Opcional | Observaciones que sean necesarias aclarar de la venta. |

## Tabla Detalle Ventas

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_detalle | Integer | 8 | PK | Identificación numérica única del renglón para el programa |
| id_venta | Integer | 8 | Fk a Ventas | Venta a la que pertenece |
| id_producto | Integer | 8 | FK a Productos | Producto vendido |
| cantidad | Integer | 8 | Mayor o igual a 0 | Unidades del producto vendido |
| precio_unitario | Float | 8 | Mayor o igual a 0 | Precio vigente del producto |
| subtotal | Float | 8 | Mayor o igual a 0 | precio_unitario x cantidad |