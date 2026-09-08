---
title: Practica 02
author: Matias Chamorro
date: "31 de agosto de 2026"
output: pdf_document
---

# Practica 02
## Historias de usuario

### _Problema 2: Cadena hotelera_

ID: `Reservar hospedaje`

Titulo: `Como` **`Usuario`** `quiero` **`Reservar hospedaje`** `para poder` **`Disfrutar unas vacaciones en el hotel`**

Reglas de negocio:
- La fecha de ingreso debe estar dentro de los 90 días a partir de la fecha actual.
- Las estadías no pueden durar más de 15 días.
---

Criterios de aceptacion: `Reservar hospedaje`

> Escenario 1: Escenario exitoso.  
- **Dado** un intento el dia 15/06/2026 de reservar hospedaje, se ingresa la fecha de ingreso 11/07/2026 y la fecha de egreso 18/07/2026, el hotel Sheraton y habitación para 4 personas. Las condiciones de pago son las adecuadas y el hotel tiene aun cupo para albergar a 4 personas.
- **Cuando** Se ingresa la fecha de ingreso 11/07/2026 y la fecha de egreso 18/07/2026, el hotel Sheraton y habitación para 4 personas y se presiona "Reservar".
- **Entonces** El sistema envia un codigo de reserva y un enlace para continuar con el pago, espera respuesta, reserva la habitacion bajo los datos proporcionados, actualiza el stock disponible de espacios en las fechas ingresadas e informa "Reserva exitosa”. 

> Escenario 2: Escenario fallido por falta de espacio.  
- **Dado** que el hotel Sheraton esta lleno.
- **Cuando** Se ingresa la fecha de ingreso 11/07/2026 y la fecha de egreso 18/07/2026, el hotel Sheraton y habitación para 4 personas y se presiona "Reservar".
- **Entonces** El sistema no realiza la reserva e informa: "No se ha podido realizar la reserva. El hotel "Sheraton" no cuenta con el espacio suficiente".

> Escenario 3: Escenario fallido por fecha muy lejana.  
- **Dado** un intento el dia 15/06/2026 de reservar hospedaje, se ingresa la fecha de ingreso 18/03/2027.
- **Cuando** Se ingresa la fecha de ingreso 18/03/2027 y la fecha de egreso 25/03/2027, el hotel Sheraton y habitación para 4 personas y se presiona "Reservar".
- **Entonces** El sistema no realiza la reserva e informa: "No se ha podido realizar la reserva. La fecha de ingreso seleccionada supera el limite de 90 dias en adelante". 

> Escenario 4: Escenario fallido por estadia muy extensa.  
- **Dado** que se ingresa la fecha de ingreso 11/07/2026 y la fecha de egreso 22/08/2026.
- **Cuando** Se ingresa la fecha de ingreso 11/07/2026 y la fecha de egreso 22/08/2026, el hotel Sheraton y habitación para 4 personas y se presiona "Reservar".
- **Entonces** El sistema no realiza la reserva e informa: "No se ha podido realizar la reserva. El periodo de estadia seleccionado supera el limite de 15 dias maximo". 

---
ID: `Realizar Check-In`

Titulo: `Como` **`Usuario`** `quiero` **`realizar el Check-In`** `para poder` **`Ser guiado hasta la habitacion asignada`**

Reglas de negocio:
- El codigo de reserva debe tener una reserva pendiente al momento de la fecha actual.
- Los check-in pueden realizarse después de las 10:00 y hasta las 23:59.

---

Criterios de aceptacion: `Realizar Check-In`

> Escenario 1: Escenario exitoso.  
- **Dado** un check-in a las 11:00 del dia 15/10/2025 y un codigo de reserva 12345 perteneciente a una reserva en el dia de la fecha.
- **Cuando** Se ingresa el codigo de reserva 12345 en la terminal del hotel y se presiona "Realizar Check-In".
- **Entonces** El sistema envia un mensaje a un conserje del hotel y a los botones, requiriendo su asistencia, e informa "Check-In exitoso”. 

> Escenario 2: Escenario fallido por codigo de reserva inexistente.  
- **Dado** un codigo de reserva 56789 que no corresponde a ninguna reserva en el dia de la fecha.
- **Cuando** Se ingresa el codigo de reserva 56789 en la terminal del hotel y se presiona "Realizar Check-In".
- **Entonces** El sistema no realiza el check-in e informa "No se ha podido realizar el check-in. El codigo de reserva no pertenece a ninguna reserva actual". 

> Escenario 3: Escenario fallido por ingreso fuera de horario.  
- **Dado** un check-in a las 9:00.
- **Cuando** Se ingresa el codigo de reserva 12345 en la terminal del hotel y se presiona "Realizar Check-In".
- **Entonces** El sistema no realiza el check-in e informa "No se ha podido realizar el check-in. Aún no se encuentran habilitados los ingresos al hotel". 

> Escenario 4: Escenario fallido por intento repetido de ingreso.  
- **Dado** un check-in a las 12:00 del dia 15/10/2025 y un codigo de reserva 9999 que pertenece a una reserva a la cual ya se le hizo check-in a las 11:00 el mismo dia.
- **Cuando** Se ingresa el codigo de reserva 999 en la terminal del hotel y se presiona "Realizar Check-In".
- **Entonces** El sistema no realiza el check-in e informa "El check-in ya ha sido realizado". 

---
ID: `Realizar Check-Out`

Titulo: `Como` **`Conserje`** `quiero` **`realizar el Check-Out`** `para poder` **`Dar por finalizada la reserva`**

Reglas de negocio:
- Solo se puede realizar check-out de habitaciones sin gastos.

---

Criterios de aceptacion: `Realizar Check-Out`

> Escenario 1: Escenario exitoso.  
- **Dado** El codigo de habitacion 11, el cual existe y pertenece a una habitacion sin ningun gasto sin abonar.
- **Cuando** Se ingresa el codigo de habitacion 11 y se presiona "Realizar Check-Out".
- **Entonces** El sistema envia un mensaje a las mucamas del hotel avisando que la habitación puede limpiarse.

> Escenario 2: Escenario fallido por habitacion con gastos a abonar pendientes.  
- **Dado** El codigo de habitacion 15 que pertenece a una habitacion con gastos por bebidas pedidas.
- **Cuando** Se ingresa el codigo de habitacion 15 y se presiona "Realizar Check-Out".
- **Entonces** El sistema no envia ningun mensaje e informa al conserje "Error: No puede hacerse el check out hasta que no se abonen los gastos realizados"

> Escenario 3: Escenario fallido por codigo de habitacion inexistente.  
- **Dado** El codigo de habitacion 158 que no pertenece a ninguna habitacion del hotel.
- **Cuando** Se ingresa el codigo de habitacion 158 y se presiona "Realizar Check-Out".
- **Entonces** El sistema no envia ningun mensaje e informa "Error al ingresar el numero de habitacion: este no pertenece a ninguna habitacion existente".

> Escenario 4: Escenario fallido por habitación libre.  
- **Dado** El codigo de habitacion 323 que pertenece a una habitacion del hotel que ya tuvo su check-out.
- **Cuando** Se ingresa el codigo de habitacion 323 y se presiona "Realizar Check-Out".
- **Entonces** El sistema no envia ningun mensaje e informa "Error al ingresar el numero de habitacion: este pertenece a una habitacion libre y sin necesidad de check-out".
