# Practica 02
## Historias de usuario

### _Problema 1: Alquiler de mobiliario_

ID: `Dar de alta Mobiliarios`

Titulo: `Como` **`Encargado de mobiliario`** `quiero` **`Dar de alta el mobiliario`** `para poder` **`Tener un registro acerca del estado del inventario`**

Reglas de negocio:
- No pueden existir codigos de inventario repetidos.
---

Criterios de aceptacion: `Dar de alta Mobiliarios`

> Escenario 1: Dado de alta exitoso.  
- **Dado** el codigo de inventario 34567 sin cargar anteriormente, fecha de creacion y de ultimo mantenimiento 02/05/2026 correcta y las condiciones son las adecuadas para dar de alta exitosamente un mobiliario.  
- **Cuando** la persona ingresa: el codigo 34567, tipo de mueble "escritorio" fecha de creacion y de ultimo mantenimiento 02/05/2025, estado libre, valor $35000 y presiona "Dar de alta".  
- **Entonces** el sistema autentica el mobiliario bajo los datos dados, lo da de alta e informa "Mobliario dado de alta correctamente".  


> Escenario 2: Dado de alta fallido por repeticion de codigo de inventario.
- **Dado** el codigo de inventario 12345 cargado anteriormente.
- **Cuando** la persona ingresa: el codigo 12345, tipo de mueble "escritorio" fecha de creacion y de ultimo mantenimiento 02/05/2025, estado libre, valor $35000 y presiona "Dar de alta".
- **Entonces** el sistema intenta autenticar el mobiliario bajo los datos dados, encuentra el codigo de inventario repetido, fallando en el proceso e informa "El codigo de inventario ya se encuentra dado de alta".

---
ID: `Generar Reserva`

Titulo: `Como` **`Cliente`** `quiero` **`Reservar un mobiliario`** `para poder` **`Amueblar mi evento`**
 
Reglas de negocio:
- Una reserva tiene que incluir como mínimo tres muebles.
- El pago de la reserva solo se puede realizar con tarjeta de crédito.
---

Criterios de aceptacion: `Generar Reserva`

> Escenario 1: Reserva exitosa.
- **Dado** Una fecha, duracion y lugar del evento correctos, un mobiliario disponible, una cantidad de al menos tres unidades y las condiciones de pago son las adecuadas para reservar exitosamente un mobiliario.
- **Cuando** la persona ingresa: la fecha 15/12/2026, 2 dias, "zona Manuel B. Gonnet", "Sillas", "tres unidades" y presiona "Reservar".
- **Entonces** el sistema redirige al usuario al pago de inscripción con tarjeta de crédito, espera respuesta, reserva el mobiliario, actualiza el stock disponible en las fechas ingresadas e informa Reserva exitosa”.

> Escenario 1: Reserva fallida por reservar menos de tres muebles.
- **Dado** Una cantidad menor a tres unidades de un mobiliario disponible.
- **Cuando** la persona ingresa: la fecha 15/12/2026, 2 dias, "zona Manuel B. Gonnet", "Sillas", "dos unidades" y presiona "Reservar".
- **Entonces** el sistema informa “No se alcanzó la cantidad minima de unidades a reservar (Tres), por lo que no se realizó la inscripción”.

> Escenario 3: Reserva fallida por no disponibilidad de suficiente mobiliario para esas fechas.
- **Dado** que para el 16/12/2026 solo quedan sin reservar dos sillas.
- **Cuando** la persona ingresa: la fecha 15/12/2026, 2 dias, "zona Manuel B. Gonnet", "Sillas", siete unidades y presiona "Reservar".
- **Entonces** el sistema informa “No hay disponibilidad suficiente de Sillas, lo sentimos.”.

> Escenario 4: Reserva fallida por error en pago.
- **Dado** Una fecha, duracion y lugar del evento correctos, un mobiliario disponible y una cantidad de al menos tres unidades, pero las condiciones de pago no son las adecuadas para reservar un mobiliario.
- **Cuando** la persona ingresa: la fecha 15/12/2026, 2 dias, "zona Manuel B. Gonnet", "Sillas", "tres unidades" y presiona "Reservar".
- **Entonces** el sistema redirige al usuario al pago de inscripción con tarjeta de crédito, espera respuesta e informa “No se ha realizado el pago correctamente, no se pudo llevar a cabo la inscripción”

---
ID: `Pago con Tarjeta`

Titulo: `Como` **`Cliente`** `quiero` **`Pagar con tarjeta`** `para poder` **`Reservar un mobiliario`**

Reglas de negocio:
- Sólo se aceptan números correspondientes a tarjetas de crédito.
- El costo de la reserva es un 20% del total del alquiler.
---

Criterios de aceptacion: `Pago con Tarjeta`

> Escenario 1: Pago exitoso
- **Dada** la conexión con el servidor del banco exitosa, el número 1234 correspondiente a una tarjeta de crédito y la tarjeta con fondos suficientes para el pago
- **Cuando** la persona ingresa el número de tarjeta 1234 y presiona “Pagar”
- **Entonces** el sistema registra el pago y retorna un resultado de éxito.

> Escenario 2: Pago fallido por número de tarjeta de crédito inexistente
- **Dado** la conexión con el servidor del banco exitosa y el número 3456 no corresponde a un número de tarjeta de crédito,
- **Cuando** el matriculado o la persona ingresa el número de tarjeta 3456 y presiona “Pagar”
- **Entonces** el sistema retorna un error por número de tarjeta inexistente.

> Escenario 3: Pago fallido por fondos insuficientes de tarjeta de crédito
- **Dada** la conexión con el servidor del banco exitosa, el número de tarjeta 2134 correspondiente a una tarjeta de crédito y sin fondos suficientes para el pago que se solicita hacer 
- **Cuando** el matriculado o la persona ingresa el número de tarjeta 2134 y presiona “Pagar”
- **Entonces** el sistema retorna un error por fondos insuficientes.

> Escenario 4: Pago fallido por fallo en la conexión con el servidor externo del banco
- **Dada** la conexión con el servidor del banco fallida
- **Cuando** el matriculado o la persona ingresa un número de tarjeta y presiona “Pagar”
- **Entonces** el sistema retorna un error por conexión no establecida.
