# Practica 02
## Historias de usuario

### _Problema 6: Pago Electrónico_

ID: `Determinar Monto`

Titulo: `Como` **`Empleado o Gerente`** `quiero` **`Recuperar los datos de una factura`** `para poder` **`Determinar el monto a cobrar`**

Reglas de negocio:
- Cuando el primer vencimiento está vencido, hay que aplicar el recargo al monto original.
- Cuando el segundo vencimiento está vencido, la factura no se puede cobrar.

---

Criterios de aceptacion: `Determinar Monto`

> Escenario 1: Escenario exitoso con factura sin vencer.  
- **Dado** 
- **Cuando** 
- **Entonces**

> Escenario 2: Escenario exitoso con factura vencida en primera fecha.  
- **Dado** 
- **Cuando** 
- **Entonces**

> Escenario 3: Escenario exitoso con factura vencida en segunda fecha.  
- **Dado** 
- **Cuando** 
- **Entonces**


---

ID: `Registrar Pago`

Titulo: `Como` **`Gerente`** `quiero` **`Registrar los pagos de los clientes`** `para poder` **`Llevar un registro`**

Reglas de negocio:
- No deben enviarse dos veces las transacciones. Deben marcarse como registradas.

---

Criterios de aceptacion: `Registrar Pago`

> Escenario 1: Escenario exitoso.  
- **Dado** Una clave maestra "ABC123" registrada en el sistema para una transacción que no fue enviada antes.
- **Cuando** el gerente ingresa: la clave maestra "ABC123" y presiona "Registrar".
- **Entonces** el sistema verifica la clave, se conecta a la central de cobro, recuperando las transacciones y servicios cobrados en el día y envíandoselas. El sistema espera respuesta y las marca como enviadas.

> Escenario 2: Escenario fallido por transacción ya enviada.  
- **Dado** Una clave maestra "WFZ345" para una transacción registrada como enviada.
- **Cuando** el gerente ingresa: la clave maestra "WFZ345" y presiona "Registrar".
- **Entonces** el sistema verifica la clave, pero no se conecta a la central de cobro, informando "Error: La transacción se encuentra marcada como enviada anteriormente".

> Escenario 3: Escenario fallido por clave no registrada.  
- **Dado** Una clave maestra "LOT789" que no está registrada en el sistema.
- **Cuando** el gerente ingresa: la clave maestra "LOT789" y presiona "Registrar".
- **Entonces** el sistema verifica la clave, pero no se conecta a la central de cobro, informando "Error: La clave maestra ingresada es incorrecta".


---

ID: `Ver Estadísticas`

Titulo: `Como` **`Gerente`** `quiero` **`Ver las estadísticas`** `para poder` **`Calcular los montos y la cantidad de cobros realizados`**

Reglas de negocio:

---

Criterios de aceptacion: `Ver Estadísticas`

> Escenario 1: Escenario exitoso.  
- **Dado** 
- **Cuando** 
- **Entonces**

> Escenario 2: Escenario fallido por mail ya registrado.  
- **Dado** 
- **Cuando** 
- **Entonces**

> Escenario 3: Escenario fallido por CUIL ya registrado.  
- **Dado** 
- **Cuando** 
- **Entonces**


---

ID: `Conectarse con Central`

Titulo: `Como` **`Sistema`** `quiero` **`Conectarme con la central`** `para poder` **`Recuperar facturas de transacciones y servicios`**

Reglas de negocio:

---

Criterios de aceptacion: `Conectarse con Central`

> Escenario 1: Escenario exitoso.  
- **Dado** 
- **Cuando** 
- **Entonces**

> Escenario 2: Escenario fallido por mail ya registrado.  
- **Dado** 
- **Cuando** 
- **Entonces**

> Escenario 3: Escenario fallido por CUIL ya registrado.  
- **Dado** 
- **Cuando** 
- **Entonces**


---