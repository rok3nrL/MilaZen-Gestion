# MilaZen-Gestion

Programa administrativo para el emprendimiento MilaZen.
Trabajo Práctico Integrador – Organización Empresarial – Tecnicatura Universitaria en Programación a Distancia (UTN).



## Descripción del sistema

MilaZen es un microemprendimiento de Río Cuarto que fabrica y vende por mayor milanesas y empanadas veganas congeladas. Hoy la administración se hace con una planilla de Excel por mes y un cuaderno, lo que dificulta comparar períodos, actualizar costos y precios a mitad de mes y conocer la rentabilidad.

El sistema propuesto es un programa de gestión, usable desde la computadora y desde el celular, que integra:

- **Productos y recetas:** precios y costos que se pueden cambiar sin alterar resultados pasados.
- **Compras, gastos y proveedores.**
- **Stock y producción:** con alertas de faltante o sobreproducción.
- **Ventas y clientes:** medios de pago y saldos pendientes.
- **Reportes de rentabilidad.**



## Integrante

- **Roberto Teodosio**



## Proceso de negocio (BPMN)

Se modeló el proceso que el sistema automatiza: el registro de una venta a un revendedor. Participan el cliente (actor externo), el propietario y el sistema. Las decisiones del proceso son: si el cliente está registrado, si hay stock suficiente, si el pago es total o parcial y si el stock queda por debajo del mínimo.

![Imagen BPMN del proceso de venta](docs/BPMN_venta.png)

[Editable BPMN del proceso de venta](docs/BPMN_venta.bpmn)



## Historias de usuario

| Historia de usuario Nº1 | Como usuario de MilaZen-Gestion, quiero registrar una venta con cliente, productos, medio de pago y monto abonado, para controlar lo vendido y lo que me deben en menos de 1 minuto. |
| Historia de usuario Nº2 | Como usuario de MilaZen-Gestion, quiero que el stock se actualice solo con cada producción y cada venta. Tambien recibir alertas, para decidir qué producir primero. |
| Historia de usuario Nº3 | Como usuario de MilaZen-Gestion, quiero cambiar precios y recetas con vigencia desde la fecha del cambio, para calcular la rentabilidad real sin alterar resultados anteriores. |

El seguimiento de estas historias (Por hacer, En progreso, Listo) está en el tablero del proyecto: `LINK DEL TABLERO`



## Indicadores de control

| Indicador | Estándar |

| Tiempo para registrar una venta habitual | 60 segundos o menos |
| Diferencia entre el stock del sistema y el stock real | 2 % o menos |
| Ventas con el saldo del cliente bien calculado | 100 % |
| Historias de usuario terminadas al cierre | 3 de 3 |
| Pull Requests revisados por otra persona antes de unirse a `main` | 100 % |

Estos estándares salen de las metas definidas en la Entrega 2 (venta en menos de 1 minuto, 2 usuarios y unos 200 registros mensuales). Si un indicador no se cumple dos veces seguidas, se crea una tarea en el tablero para corregirlo.



## Declaración de Uso de IA

Se usó **Claude** como asistente para organizar la Entrega 4, armar la idea del diagrama BPMN, hacer uso de github, desarrollar un README.md prolijo y corregir redacción y ortografía.

**Prompts utilizados y por qué:**

1. Le pasé la consigna de la Entrega 4, y que me ayudar a pensar los pasos del proceso de venta para hacer el diagrama BPMN.
2. Le pedí ayuda para redactar un README.md profesional guiandose por mi trabajo realziado hasta el TP nº 3.
3. Le pedi que me ayudara con el uso de github y git por consola.

**Correcciones que hice yo sobre lo que generó la IA:**

- Se borraron muchas cosas inesesarias y otras que si eran utiles se simplificaron.
- Se fue corroborando paso a paso la guia en el uso de git y aprendiendo en el proceso.
- 