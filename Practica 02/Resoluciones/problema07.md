# Practica 02
## Historias de usuario

### _Problema 7: Transferencias vehiculares_

ID: `Transferir Vehículo`

Titulo: `Como` **`Usuario`** `quiero` **`Transferir un vehículo`** `para poder` **`Venderlo`**

Reglas de negocio:
- La patente ingresada no debe tener deudas.
- Tanto el vendedor como el comprador deben ser mayores de 18 años.

---

Criterios de aceptacion: `Transferir Vehículo`

> Escenario 1: Escenario exitoso.  
- **Dado** un usuario autenticado vendedor DNI 24486555, mayor de 18 años, un comprador DNI 38355364, también mayor de edad, y una patente AC640PQ existente y sin deudas.
- **Cuando** El usuario se debe ingresar la patente AC640PQ, el DNI 24486555 del vendedor y el DNI 38355364 del comprador y presiona "Transferir".
- **Entonces** El sistema realiza la transferencia con éxito y se le envía al mail del comprador un código AFD908 para que realice el pago.

> Escenario 2: Escenario fallido por vendedor menor de edad.  
- **Dado** un usuario autenticado vendedor DNI 51486555, menor de 18 años y un comprador DNI 38355364, mayor de edad.
- **Cuando** El usuario se debe ingresar la patente AC640PQ, el DNI 51486555 del vendedor y el DNI 38355364 del comprador y presiona "Transferir".
- **Entonces** El sistema no realiza la transferencia, informando "Error: el vendedor es menor de 18 años".

> Escenario 3: Escenario fallido por comprador menor de edad.  
- **Dado** un usuario autenticado vendedor DNI 21486555, mayor de 18 años y un comprador DNI 58355364, menor de edad.
- **Cuando** El usuario se debe ingresar la patente AC640PQ, el DNI 21486555 del vendedor y el DNI 58355364 del comprador y presiona "Transferir".
- **Entonces** El sistema no realiza la transferencia, informando "Error: el comprador es menor de 18 años".

> Escenario 4: Escenario fallido por patente con deudas pendientes.  
- **Dado** una patente AD123RT existente que tiene tres deudas pendientes.
- **Cuando** El usuario se debe ingresar la patente AD123RT, el DNI 24486555 del vendedor y el DNI 38355364 del comprador y presiona "Transferir".
- **Entonces** El sistema no realiza la transferencia, informando "Error: La patente ingresada tiene deuda/s pendiente/s a pagar".

> Escenario 5: Escenario fallido por patente inexistente.  
- **Dado** una patente AX094YY que no existe.
- **Cuando** El usuario se debe ingresar la patente fallido, el DNI 24486555 del vendedor y el DNI 38355364 del comprador y presiona "Transferir".
- **Entonces** El sistema no realiza la transferencia, informando "Error: La patente ingresada no existe".

---

ID: `Consultar Transferencia`

Titulo: `Como` **`Usuario`** `quiero` **`Consultar una transferencia`** `para poder` **`Saber su estado`**

Reglas de negocio:
- Se pueden hacer hasta tres consultas por mes.

---

Criterios de aceptacion: `Consultar Transferencia`

> Escenario 1: Escenario exitoso.  
- **Dada** la patente AE987CD que existe, la cual fue consultada una vez en el mes.
- **Cuando** el usuario ingresa una patente AE987CD y presiona "Consultar".
- **Entonces** el sistema informa en pantalla el estado de la transferencia.

> Escenario 2: Escenario fallido por patente inexistente.  
- **Dada** la patente AH456LS que no existe.
- **Cuando** el usuario ingresa una patente AH456LS y presiona "Consultar".
- **Entonces** el sistema no encuentra la patente e informa "Error: La patente ingresada no existe".

> Escenario 3: Escenario fallido por más de tres consultas mensuales.  
- **Dada** la patente AI203FF que existe, la cual fue consultada tres veces en el mes.
- **Cuando** el usuario ingresa una patente AI203FF y presiona "Consultar".
- **Entonces** el sistema informa "Error: La patente ingresada ya fue consultada tres veces en el mes".


---