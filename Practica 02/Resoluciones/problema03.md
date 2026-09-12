---
title: Practica 02
author: Matias Chamorro
date: "31 de agosto de 2026"
output: pdf_document
---

# Practica 02
## Historias de usuario

### _Problema 3: Venta de bebidas_

ID: `Registrar Usuario`

Titulo: `Como` **`Persona`** `quiero` **`Crearme una cuenta`** `para poder` **`Empezar a comprar en el sitio`**

Reglas de negocio:
- El mail no debe repetirse, será usado como nombre de usuario.
- Solo se permite que se registren al sitio personas mayores a 18 años.
---

Criterios de aceptacion: `Registrar Usuario`

> Escenario 1: Escenario exitoso.  
- **Dado** un mail pedro123@gmail.com no registrado previamente y un mayor de 18 años.
- **Cuando** la persona ingresa: nombre Pedro, apellido Gómez, mail pedro123@gmail.com, edad 20 años y presiona "Registrar".
- **Entonces** el sistema crea la cuenta y genera una contraseña y la envía al mail ingresado, informando "El registro se ha realizado correctamente".

> Escenario 2: Escenario fallido por mail ya registrado.  
- **Dado** un mail martinABC@gmail.com registrado previamente.
- **Cuando** la persona ingresa: nombre Martín, apellido Correa, mail martinABC@gmail.com, edad 21 años y presiona "Registrar".
- **Entonces** el sistema no crea una cuenta e informa "Error: el mail martinABC@gmail.com ha sido registrado anteriormente."
 
> Escenario 3: Escenario fallido por menor a 18 años.  
- **Dado** un menor de 18 años.
- **Cuando** la persona ingresa: nombre Sebastián, apellido Martínez, mail sebasMart@gmail.com, edad 17 años y presiona "Registrar".
- **Entonces** el sistema no crea una cuenta e informa "Error: la edad mínima para crear una cuenta es 18 años" y muestra en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores.

---
ID: `Iniciar Sesión`

Titulo: `Como` **`Usuario`** `quiero` **`Ingresar a la página`** `para poder` **`Usar el sistema de compras en línea`**

Reglas de negocio:
- El nombre de usuario debe pertenecer a una cuenta existente.

---

Criterios de aceptacion: `Iniciar Sesión`

> Escenario 1: Escenario exitoso.  
- **Dado** un mail "pepito6767@gmail.com" ya registrado y su contraseña  correspondiente.
- **Cuando** el usuario ingresa el mail "pepito6767@gmail.com", su contraseña "6767" y presiona "Iniciar sesión".
- **Entonces** el sistema comprueba los datos ingresados y redirige al usuario a la lista de bebidas.

> Escenario 2: Escenario fallido por mail no registrado.  
- **Dado** un mail "soymia@gmail.com" no registrado.
- **Cuando** el usuario ingresa el mail "soymia@gmail.com", su contraseña "123" y presiona "Iniciar sesión".
- **Entonces** el sistema comprueba los datos ingresados e informa "No se pudo iniciar sesión. El mail o la contraseña son incorrectos".

> Escenario 2: Escenario fallido por contraseña incorrecta.  
- **Dado** un mail "papazanahoria@gmail.com" registrado con la contraseña "vegetales".
- **Cuando** el usuario ingresa el mail "papazanahoria@gmail.com", su contraseña "vegetales" y presiona "Iniciar sesión".
- **Entonces** el sistema comprueba los datos ingresados e informa "No se pudo iniciar sesión. El mail o la contraseña son incorrectos".

---
ID: `Comprar bebidas`

Titulo: `Como` **`Usuario`** `quiero` **`Seleccionar los productos`** `para poder` **`Comprarlos en línea`**

Reglas de negocio:
- Si el usuario es premium, se le hace un descuento del 20%.
- Si el usuario seleccionó productos por un monto superior a los $4500, se le hace un 10% de descuento .
- Los descuentos son acumulables.

---

Criterios de aceptacion: `Comprar bebidas`

> Escenario 1: Escenario sin descuentos.  
- **Dado** un usuario no premium con una compra con un valor total por $3500.
- **Cuando** el usuario selecciona sus bebidas deseadas y presiona "Informar monto total"
- **Entonces** el sistema informa en pantalla "Monto total: $3500"

> Escenario 2: Escenario con descuento por usuario premium.  
- **Dado** un usuario premium con una compra con un valor total por $4000.
- **Cuando** el usuario selecciona sus bebidas deseadas y presiona "Informar monto total"
- **Entonces** el sistema informa en pantalla "Monto total: $3200"

> Escenario 3: Escenario con descuento por monto mayor a $4500.  
- **Dado** un usuario no premium con una compra con un valor total por $5500.
- **Cuando** el usuario selecciona sus bebidas deseadas y presiona "Informar monto total"
- **Entonces** el sistema informa en pantalla "Monto total: $4950"

> Escenario 4: Escenario con acumulación de ambos descuentos.  
- **Dado** un usuario premium con una compra con un valor total por $12000.
- **Cuando** el usuario selecciona sus bebidas deseadas y presiona "Informar monto total"
- **Entonces** el sistema informa en pantalla "Monto total: $8640"


---
ID: `Cerrar Sesión`

Titulo: `Como` **`Usuario`** `quiero` **`Cerrar mi sesión`** `para poder` **`Salir de mi cuenta`**

Reglas de negocio:

---

Criterios de aceptacion: `Cerrar Sesión`

> Escenario 1: Escenario exitoso.  
- **Dado** un usuario que ha iniciado sesión antes.
- **Cuando** el usuario presiona "Cerrar sesión".
- **Entonces** el sistema cierra la sesión y redirige al usuario a la pantalla de inicio de sesión.


---