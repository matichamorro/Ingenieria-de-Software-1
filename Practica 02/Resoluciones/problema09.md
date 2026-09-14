# Practica 02
## Historias de usuario

### _Problema 9: Créditos bancarios_

ID: `Pedir Crédito`

Titulo: `Como` **`Persona o Cliente`** `quiero` **`Iniciar un trámite a través de un sitio web`** `para poder` **`Pedir un Crédito`**

Reglas de negocio:
- El dni ingresado debe corresponder a un cliente del banco.
- El crédito solicitado no debe superar los $400.000.

---

Criterios de aceptacion: `Pedir Crédito`

> Escenario 1: Escenario exitoso.  
- **Dado** un DNI 23.364.456 y un mail "marcel4@gmail.com", los cuales pertenecen a una cliente del banco y un crédito solicitado de $300.000.
- **Cuando** la persona ingresa: DNI 23.364.456, nombre "Marcela", apellido "Pagani", mail "marcel4@gmail.com", tipo de crédito "personal" y un monto de $300.000 y presiona "Solicitar crédito".
- **Entonces** el sistema almacena el trámite e imprime un número de comprobante 003984 para el cliente.

> Escenario 2: Escenario fallido por DNI no registrado como cliente.  
- **Dado** un DNI 23.364.456 que no pertenece a un cliente del banco.
- **Cuando** la persona ingresa: DNI 23.364.456, nombre "Marcela", apellido "Pagani", mail "marcel4@gmail.com", tipo de crédito "personal" y un monto de $300.000 y presiona "Solicitar crédito".
- **Entonces** el sistema rechaza el inicio de trámite y envía un correo electrónico al email ingresado con un instructivo para hacerse cliente del banco.

> Escenario 3: Escenario fallido por crédito mayor a los $400.000.  
- **Dado** un crédito solicitado de $800.000.
- **Cuando** la persona ingresa: DNI 23.364.456, nombre "Marcela", apellido "Pagani", mail "marcel4@gmail.com", tipo de crédito "personal" y un monto de $800.000 y presiona "Solicitar crédito".
- **Entonces** el sistema rechaza el inicio de trámite e imprime en pantalla el mensaje “Error: El monto solicitado excede el límite permitido ($300.000)”

---

ID: `Registrar Cliente`

Titulo: `Como` **`Persona`** `quiero` **`Registrarme en la página`** `para poder` **`Hacerme cliente y poder pedir créditos`**

Reglas de negocio:

---

Criterios de aceptacion: `Registrar Cliente`

> Escenario 1: Escenario exitoso.  
- **Dado** un DNI 23.364.456 y un mail "marcel4@gmail.com", los cuales no están registrados anteriormente.
- **Cuando** la persona ingresa: DNI 23.364.456, nombre "Marcela", apellido "Pagani", mail "marcel4@gmail.com" y presiona "Registrarse".
- **Entonces** El sistema crea la cuenta e informa en pantalla "Cuenta creada correctamente", redirigiendo al cliente nuevamente a la página de solicitudes de créditos.

> Escenario 2: Escenario fallido por DNI ya registrado.  
- **Dado** un DNI 23.364.456 que ya está registrado anteriormente.
- **Cuando** la persona ingresa: DNI 23.364.456, nombre "Marcela", apellido "Pagani", mail "marcel4@gmail.com" y presiona "Registrarse".
- **Entonces** El sistema no crea una cuenta e informa en pantalla "Error: el DNI ya está registrado anteriormente".

> Escenario 3: Escenario fallido por mail ya registrado.  
- **Dado** un mail "marcel4@gmail.com" que ya está registrado anteriormente.
- **Cuando** la persona ingresa: DNI 23.364.456, nombre "Marcela", apellido "Pagani", mail "marcel4@gmail.com" y presiona "Registrarse".
- **Entonces** El sistema no crea una cuenta e informa en pantalla "Error: el mail ya está registrado anteriormente". 


---

ID: `Consultar Estado`

Titulo: `Como` **`Cliente`** `quiero` **`Consultar el estado de un trámite`** `para poder` **`Generar un informe del mismo`**

Reglas de negocio:
- El cliente no puede ingresar tres veces un número inexistente, sino se bloquearía su ip por 24 horas.

---

Criterios de aceptacion: `Consultar Estado`

> Escenario 1: Escenario exitoso.  
- **Dado** un cliente con cero consultas por un número inexistente de comprobante y el número de comprobante 003984 existente en el sistema.
- **Cuando** el cliente ingresa un número de comprobante 003984 y presiona "Consultar estado".
- **Entonces** el sistema retorna un informe con el estado del trámite con el número ingresado.

> Escenario 2: Escenario fallido con menos de tres ingresos de números inexistentes.  
- **Dado** un cliente con una consulta por un número inexistente de comprobante y el número de comprobante 005687 inexistente en el sistema.
- **Cuando** el cliente ingresa un número de comprobante 005687 y presiona "Consultar estado".
- **Entonces** el sistema verifica e informa en pantalla “trámite inexistente”.

> Escenario 3: Escenario fallido con tres ingresos de números inexistentes.  
- **Dado** un cliente con dos consultas por un número inexistente de comprobante y el número de comprobante 005687 inexistente en el sistema.
- **Cuando** el cliente ingresa un número de comprobante 005687 y presiona "Consultar estado".
- **Entonces** el sistema verifica e informa en pantalla “Trámite inexistente”, bloqueando la ip del cliente por 24 horas, y también imprimiendo “Usted ha excedido el número de consultas inválidas”.

> Escenario 4: Escenario fallido por IP bloqueada.  
- **Dado** un cliente al cual se le bloqueó su IP anteriormente.
- **Cuando** el cliente ingresa un número de comprobante 005687 y presiona "Consultar estado".
- **Entonces** el sistema verifica e informa en pantalla "Usted ha excedido el número de consultas inválidas”.


---

ID: `Pedir Listado`

Titulo: `Como` **`Gerente del banco`** `quiero` **`Pedir un listado de créditos aprobados`** `para poder` **`Visualizar la información general del banco`**

Reglas de negocio:
- Las fechas ingresadas deben ser válidas.

---

Criterios de aceptacion: `Pedir Listado`

> Escenario 1: Escenario exitoso.  
- **Dado** un pedido del listado el día 15/10/2026 y 20 créditos solicitados el 21/9/2026.
- **Cuando** el gerente ingresa el rango de fechas: del 19/9/2026 al 25/9/2026 y presiona "Listado de créditos".
- **Entonces** el sistema mostrará un listado con los créditos aprobados

> Escenario 2: Escenario fallido con 0 créditos aprobados en las fechas ingresadas.  
- **Dado** un pedido del listado el día 15/10/2026 y 0 créditos solicitados el 21/9/2026.
- **Cuando** el gerente ingresa el rango de fechas: del 19/9/2026 al 25/9/2026 y presiona "Listado de créditos".
- **Entonces** el sistema imprime el mensaje: ”No hay créditos aprobados en las fechas ingresadas”.

> Escenario 3: Escenario fallido con fechas inválidas.  
- **Dado** un pedido del listado el día 15/9/2026.
- **Cuando** el gerente ingresa el rango de fechas: del 19/9/2026 al 25/9/2026 y presiona "Listado de créditos".
- **Entonces** el sistema no genera ningún listado e imprime el mensaje “las fechas ingresadas no son válidas”


---