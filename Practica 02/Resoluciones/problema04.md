# Practica 02
## Historias de usuario

### _Problema 4: Préstamos de Kits_

ID: `Solicitar Kit`

Titulo: `Como` **`Usuario`** `quiero` **`Solicitar un kit multimedia`** `para poder` **`usarlo en trabajos académicos`**

Reglas de negocio:
- Los préstamos no pueden durar más de 3 horas.
- No se puede solicitar un préstamo si existe algún préstamo anterior activo.

---

Criterios de aceptacion: `Solicitar Kit`

> Escenario 1: Escenario exitoso.  
- **Dado** un usuario sin préstamos todavía activos y un préstamo de 2 horas.
- **Cuando** el usuario ingresa: tipo de kit avanzado, día 15/10, hora de retiro 12:00, una duración de 2 horas y presiona "Solicitar".
- **Entonces** el sistema verifica los datos ingresados, crea la solicitud e informa "Solicitud aceptada para el día 15/10".

> Escenario 2: Escenario fallido por préstamo muy extenso.  
- **Dado** un préstamo de 12 horas.
- **Cuando** el usuario ingresa: tipo de kit básico, día 5/6, hora de retiro 11:00, una duración de 12 horas y presiona "Solicitar".
- **Entonces** el sistema verifica los datos ingresados, no crea la solicitud e informa "Error: no se pueden solicitar préstamos de más de 3 horas".
 
> Escenario 3: Escenario fallido por préstamo anterior activo.  
- **Dado** un usuario con un préstamo anterior activo.
- **Cuando** el usuario ingresa: tipo de kit básico, día 15/9, hora de retiro 13:00, una duración de 2 horas y presiona "Solicitar".
- **Entonces** el sistema verifica los datos ingresados, no crea la solicitud e informa "Error: no se pueden solicitar préstamos si ya tiene uno activo".

> Escenario 4: Escenario fallido por falta de stock.  
- **Dado** un usuario sin préstamos todavía activos y un préstamo de 2 horas.
- **Cuando** el usuario ingresa: tipo de kit avanzado, día 9/11, hora de retiro 10:00, una duración de 2 horas y presiona "Solicitar".
- **Entonces** el sistema verifica los datos ingresados, no crea la solicitud e informa "Lo sentimos, no tenemos stock de kit avanzado para el día 9/11. Intente otro día".

---
ID: `Agregar Elementos`

Titulo: `Como` **`Administrador`** `quiero` **`Poder agregar elementos`** `para poder` **`Hacer que formen parte de un kit`**

Reglas de negocio:
- El número de serie no puede repetirse.
- El precio de compra no puede superar el millón de pesos.
- Si el elemento no es nacional, deberá agregarse un impuesto adicional del 10%.

---

Criterios de aceptacion: `Agregar Elementos`

> Escenario 1: Escenario exitoso con producto nacional.  
- **Dado** un número de serie 0655 sin repetirse, un precio de compra de 300.000 pesos y un producto nacional.
- **Cuando** el usuario ingresa: número de serie 0655, cámara, precio $300.000, origen nacional y fecha de alta 11/8/2026. 
- **Entonces** el sistema agrega correctamente el producto e informa "Elemento agregado correctamente".

> Escenario 2: Escenario exitoso con producto internacional.  
- **Dado** un número de serie 8954 sin repetirse, un precio de compra de 800.000 pesos y un producto internacional.
- **Cuando** el usuario ingresa: número de serie 8954, trípode, precio $800.000, origen internacional y fecha de alta 18/2/2026. 
- **Entonces** el sistema agrega correctamente el producto y guarda un impuesto de $80.000, informando "Elemento agregado correctamente".

> Escenario 3: Escenario fallido por número de serie repetido.  
- **Dado** un número de serie 2222 ya agregado anteriormente.
- **Cuando** el usuario ingresa: número de serie 2222, micrófono, precio $200.000, origen internacional y fecha de alta 20/3/2026
- **Entonces** el sistema no agrega el producto, informando "Error: el número de serie ya fue agregado anteriormente. Por favor ingrese otro".

> Escenario 4: Escenario fallido por precio de compra muy alto.  
- **Dado** un precio de compra de 1.800.000 pesos.
- **Cuando** el usuario ingresa: número de serie 4679, micrófono, precio $1.800.000, origen nacional y fecha de alta 21/12/2026
- **Entonces** el sistema no agrega el producto, informando "Error: el precio de compra supera el millón de pesos".