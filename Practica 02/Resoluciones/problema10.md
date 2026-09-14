# Practica 02
## Historias de usuario

### _Problema 10: Manejo de canchas de tenis_

ID: `Registrar Cuenta`

Titulo: `Como` **`Persona`** `quiero` **`Registrar mi cuenta`** `para poder` **`Ingresar a la página`**

Reglas de negocio:
- Solo pueden registrarse personas mayores de 18 años.

---

Criterios de aceptacion: `Registrar Cuenta`

> Escenario 1: Escenario exitoso.  
- **Dado** un mail "gusRamirZ@gmail.com" no registrado y una persona con 20 años.
- **Cuando** la persona ingresa: "Gustavo", "Ramírez", "gusRamirZ@gmail.com", "20 años" y "47 e/17 y 18 n°2898" y presiona "Registrarse".
- **Entonces** el sistema verifica los datos, registra una cuenta y genera una contraseña "asfASF" que es enviada al mail ingresado.

> Escenario 2: Escenario fallido por mail ya registrado.  
- **Dado** un mail "gusRamirZ@gmail.com" ya registrado.
- **Cuando** la persona ingresa: "Gustavo", "Ramírez", "gusRamirZ@gmail.com", "20 años" y "47 e/17 y 18 n°2898" y presiona "Registrarse".
- **Entonces** el sistema no registra la cuenta e informa "El mail ya ha sido registrado anteriormente".

> Escenario 3: Escenario fallido por tener menos de 18 años.  
- **Dada** una persona con 16 años.
- **Cuando** la persona ingresa: "Gustavo", "Ramírez", "gusRamirZ@gmail.com", "16 años" y "47 e/17 y 18 n°2898" y presiona "Registrarse".
- **Entonces** el sistema no registra la cuenta e informa "Lo sentimos, no puede registrarse si no es mayor de 18 años".


---

ID: `Iniciar Sesión`

Titulo: `Como` **`Persona`** `quiero` **`Iniciar sesión en mi cuenta`** `para poder` **`Usar la página`**

Reglas de negocio:
- Si un usuario falla tres veces al iniciar sesión su cuenta sea bloqueada

---

Criterios de aceptacion: `Iniciar Sesión`

> Escenario 1: Escenario exitoso.  
- **Dado** un mail "gusRamirZ@gmail.com" registrado, cuya cuenta no está bloqueada, y su contraseña "asfASF".
- **Cuando** una persona ingresa: "gusRamirZ@gmail.com", "asfASF" y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos y redirige al usuario a la página de reserva de turnos.

> Escenario 2: Escenario fallido por mail no registrado y menos de tres fallos.  
- **Dado** una persona que no falló en iniciar sesión, un mail "gusRamirZ@gmail.com" no registrado.
- **Cuando** una persona ingresa: "gusRamirZ@gmail.com", "asfASF" y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos e informa "Error: el mail o la contraseña ingresados no son correctos".

> Escenario 3: Escenario fallido por contraseña incorrecta y menos de tres fallos.  
- **Dado** una persona que no falló en iniciar sesión, un mail "gusRamirZ@gmail.com" registrado y su contraseña "asfASF".
- **Cuando** una persona ingresa: "gusRamirZ@gmail.com", "ert457" y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos e informa "Error: el mail o la contraseña ingresados no son correctos".

> Escenario 4: Escenario fallido con tres fallos.  
- **Dado** una persona que falló tres veces en iniciar sesión, un mail "gusRamirZ@gmail.com" registrado y su contraseña "asfASF".
- **Cuando** una persona ingresa: "gusRamirZ@gmail.com", "ert457" y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos e informa "Error: el mail o la contraseña ingresados no son correctos", y también "Error: Muchos intentos fallidos... La cuenta se encuentra bloqueada".

> Escenario 5: Escenario fallido por cuenta bloqueada.  
- **Dado** un mail "gusRamirZ@gmail.com" registrado cuya cuenta está bloqueada.
- **Cuando** una persona ingresa: "gusRamirZ@gmail.com", "ert457" y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos e informa "Error: Muchos intentos fallidos... La cuenta se encuentra bloqueada".

---

ID: `Obtener Turno`

Titulo: `Como` **`Usuario`** `quiero` **`Obtener un turno`** `para poder` **`Reservar una cancha de tenis`**

Reglas de negocio:
- No se puede dar turno con menos de 2 días a la fecha en que se solicita.

---

Criterios de aceptacion: `Obtener Turno`

> Escenario 1: Escenario exitoso.  
- **Dado** que el día 16/9/2026 se quiere reservar "cancha 3", para el día 19/9/2026, que se encuentra libre.
- **Cuando** el usuario ingresa: "cancha 3", fecha 19/9/2026, hora 12:00 y presiona "Obtener turno".
- **Entonces** el sistema registra la reserva a nombre del usuario e imprime "Su turno ha sido registrado con éxito".

> Escenario 2: Escenario fallido por cancha ya reservada.  
- **Dado** que el día 16/9/2026 se quiere reservar "cancha 3", para el día 19/9/2026, que se encuentra ocupada.
- **Cuando** el usuario ingresa: "cancha 3", fecha 19/9/2026, hora 12:00 y presiona "Obtener turno".
- **Entonces** el sistema imprime "Cancha ocupada, por favor seleccione otro día y horario", mostrando nuevamente la pantalla de selección de turnos.

> Escenario 3: Escenario fallido por reserva con poca antelación.  
- **Dado** que el día 16/9/2026 se quiere reservar "cancha 3" para el día 17/9/2026.
- **Cuando** el usuario ingresa: "cancha 3", fecha 17/9/2026, hora 12:00 y presiona "Obtener turno".
- **Entonces** el sistema imprime "Lo sentimos, no puede reservar con menos de 2 días de antelación", mostrando nuevamente la pantalla de selección de turnos.


---

ID: `Cerrar Sesión`

Titulo: `Como` **`Usuario`** `quiero` **`Cerrar mi sesión`** `para poder` **`Cerrar el acceso a mi cuenta`**

Reglas de negocio:

---

Criterios de aceptacion: `Obtener Turno`

> Escenario 1: Escenario exitoso.  
- **Dado** Un usuario que inició sesión previamente.
- **Cuando** el usuario presiona "Cerrar sesión".
- **Entonces** el sistema redirige al usuario a la pantalla de inicio de sesión.

---