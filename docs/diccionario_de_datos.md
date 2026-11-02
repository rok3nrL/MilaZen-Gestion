## Tabla Productos

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_producto | Integer | 8 | PK | Identificación numérica única del producto para el programa |
| nombre | String | 50 | Obligatorio | Nombre comercial, para facilitar su búsqueda y reconocimiento dentro del programa |
| categoria | String | 20 | Milanesas / Empanadas | División en categorías, facilita la visualización de ventas por separado |
| id_precio | Integer | 8 | FK a Historial Precios | Precio de venta que apunta a la última actualización de Historial Precios |
| stock | Integer | 8 | Mayor o igual que 0 | Contabilización de unidades disponibles, sube con producción, baja con ventas |
| id_receta | Integer | 8 | FK a Recetas | Receta vigente con costo a la fecha. |
| unidad_x_bulto | Integer | 8 | Mayor que 0 | Unidades que contiene cada paquete, útil para calcular costos y rentabilidad |
| codigo_barra | String | 13 | Único | Código de barra único para identificar producto con lectora |
| activo | Boolean | - | True/False | Producto activo o inactivo |

## Tabla Materia Prima

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_materia_prima | Integer | 8 | PK | Identificación numérica única de la materia prima |
| nombre | String | 20 | Obligatorio / Único | Nombre, para facilitar su búsqueda y reconocimiento |
| id_proveedor | Integer | 8 | FK a proveedor, opcional | Proveedor, facilita el seguimiento de deuda y pagos |
| id_costo | Integer | 8 | FK a Historial Costos | Precio de costo vigente a la fecha. |
| stock | Float | 8 | Mayor o igual que 0 | Contabilización de unidades disponibles, sube con compra, baja con producción |
| unidad_medida | String | 8 | Kg o unidad | Unidad en que se va a medir |
| unidad_x_bulto | Float | 8 | Mayor que 0 | Cantidad de unidades o peso del bulto de materia prima |

## Tabla Recetas

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_receta | Integer | 8 | PK | Identificación numérica única de la receta para el programa |
| id_producto | Integer | 8 | FK a Productos | Producto elaborado |
| costo_final | Float | 8 | Mayor o igual que 0 | Suma de todos los costos materia prima de Detalle Recetas. |
| fecha_desde | Date | - | Obligatorio / dd/mm/aaaa | Fecha desde la que rige la receta |

## Tabla Detalle Recetas

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_detalle_receta | Integer | 8 | PK | Identificación numérica única del detalle de la receta |
| id_receta | Integer | 8 | FK a Recetas | Versión de receta con la que se relaciona |
| id_materia_prima | Integer | 8 | FK a Materia Prima | Ingrediente |
| cantidad | Float | 8 | Mayor que 0 / unidad o KG | Cantidad por unidad o KG |
| costo_materia_prima | Float | 8 | Mayor o igual que 0 | Cantidad x costo vigente de la materia prima |

## Tabla Historial Precios

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_precio | Integer | 8 | PK | Identificación de la modificación de los precios |
| id_producto | Integer | 8 | FK a Productos | Identificación del producto al que pertenece el precio |
| precio_revendedor | Float | 8 | Mayor que 0 | Precio revendedor desde fecha |
| precio_consumidor_f | Float | 8 | Mayor que 0 | Precio consumidor final desde fecha |
| fecha_desde | Date | - | Obligatorio / dd/mm/aaaa | Fecha desde la que rigen precios revendedor y consumidor final |

## Tabla Historial Costos

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_costo | Integer | 8 | PK | Identificación de la modificación del costo |
| id_materia_prima | Integer | 8 | FK a Materia Prima | Identificación de la materia prima al que pertenece el costo |
| precio_costo | Float | 8 | Mayor que 0 | Costo materia prima desde fecha |
| fecha_desde | Date | - | Obligatorio / dd/mm/aaaa | Fecha desde la que rige costo de la materia prima |

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
| fecha | Date | - | Formato dd/mm/aaaa | Fecha de la venta realizada |
| medio_pago | String | 20 | Efectivo / Transferencia | Forma de abonar del cliente |
| total | Float | 8 | Mayor o igual que 0 | Total de la venta a abonar (Suma de subtotales de Detalle Ventas) |
| pago | Boolean | - | True / False | True -> se descuenta el total. False -> se utiliza monto pagado o cliente adeuda el total |
| monto_pagado | Float | 8 | Mayor o igual que 0 | En caso de no abonar el total, sirve para descontar del total |
| observaciones | String | 200 | Opcional | Observaciones que sean necesarias aclarar de la venta |

## Tabla Detalle Ventas

| Campo | Tipo | Longitud | Restricción / Valores | Descripción Funcional |
|---|---|---|---|---|
| id_detalle | Integer | 8 | PK | Identificación numérica única del renglón para el programa |
| id_venta | Integer | 8 | FK a Ventas | Venta a la que pertenece |
| id_producto | Integer | 8 | FK a Productos | Producto vendido |
| cantidad | Integer | 8 | Mayor o igual a 0 | Unidades del producto vendido |
| precio_unitario | Float | 8 | Mayor o igual a 0 | Precio vigente del producto |
| subtotal | Float | 8 | Mayor o igual a 0 | precio_unitario * cantidad |