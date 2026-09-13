# Practica 02
## Historias de usuario

### _Problema 5: Manejo de licencias_

ID: `Registrar Cuenta`

Titulo: `Como` **`Persona`** `quiero` **`Registrame`** `para poder` **`Tener una cuenta en la página`**

Reglas de negocio:

---

Criterios de aceptacion: `Registrar Cuenta`

> Escenario 1: Escenario exitoso.  
- **Dado** un mail pepePepito@yahoo.com y un CUIL 20-29863333-7 no registrados anteriormente.
- **Cuando** el usuario ingresa: mail pepePepito@yahoo.com, CUIL 20-29863333-7, contraseña pepo y presiona "Registrarse".
- **Entonces** el sistema verifica los datos y crea una cuenta, informando "Cuenta creada exitosamente".

> Escenario 2: Escenario fallido por mail ya registrado.  
- **Dado** un mail carlaGamer@gmail.com registrado anteriormente.
- **Cuando** el usuario ingresa: mail carlaGamer@gmail.com, CUIL 27-38347523-2, contraseña carlaa123 y presiona "Registrarse".
- **Entonces** el sistema verifica los datos pero no crea una cuenta, informando "Error: el mail ingresado ya se encuentra registrado".
 
> Escenario 3: Escenario fallido por CUIL ya registrado.  
- **Dado** un CUIL 23-42993049-6 registrado anteriormente.
- **Cuando** el usuario ingresa: mail brunoo000@gmail.com, CUIL 23-42993049-6, contraseña brun0 y presiona "Registrarse".
- **Entonces** el sistema verifica los datos pero no crea una cuenta, informando "Error: el número de CUIL ingresado ya se encuentra registrado".


---

ID: `Iniciar Sesión`

Titulo: `Como` **`Usuario`** `quiero` **`Iniciar sesión`** `para poder` **`Ingresar a la página de licencias médicas`**

Reglas de negocio:

---

Criterios de aceptacion: `Iniciar Sesión`

> Escenario 1: Escenario exitoso.  
- **Dado** el mail brunoo000@gmail.com ya registrado, bajo la contraseña brun0.
- **Cuando** el usuario ingresa: mail brunoo000@gmail.com, contraseña brun0 y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos y redirige al usuario a la página para el seguimiento de pedidos de licencias médicas.

> Escenario 2: Escenario fallido por mail no registrado.  
- **Dado** el mail totoro@gmail.com no registrado en el sistema.
- **Cuando** el usuario ingresa: mail totoro@gmail.com, contraseña toto y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos e informa "Error: el mail o la contraseña son inválidos"
 
> Escenario 3: Escenario fallido por contraseña inválida.  
- **Dado** el mail zoe333@gmail.com registrado en el sistema con la contraseña zoe345.
- **Cuando** el usuario ingresa: mail zoe333@gmail.com, contraseña zoe333 y presiona "Iniciar sesión".
- **Entonces** el sistema verifica los datos e informa "Error: el mail o la contraseña son inválidos"


---

ID: `Solicitar Licencia`

Titulo: `Como` **`Empleado`** `quiero` **`Solicitar una licencia`** `para poder` **`Tener un período de recuperación`**

Reglas de negocio:
- El empleado debe tener más de 1 mes de antigüedad.
- El empleado no debe tener una licencia anterior vigente.

---

Criterios de aceptacion: `Solicitar Licencia`

> Escenario 1: Escenario exitoso.  
- **Dado** Un empleado con 6 meses de antigüedad y sin licencias anteriores vigentes.
- **Cuando** el empleado ingresa: tipo de licencia presencial, la fecha de inicio de reposo 12/8/2025, la matrícula 138580, el diagnóstico "pierna rota" y "para el titular", y presiona "Solicitar".
- **Entonces** el sistema verifica el estado del empleado, genera un código de licencia 7637 y lo envía via mail a la casilla del empleado, junto con la confirmación de la licencia y los días otorgados.

> Escenario 2: Escenario fallido por falta de antigüedad del empleado.  
- **Dado** Un empleado con 15 días de antigüedad.
- **Cuando** el empleado ingresa: el tipo de licencia telemedicina, la fecha de inicio de reposo 12/8/2025, la matrícula 138457, el diagnóstico "pierna rota" y "para el titular", y presiona "Solicitar".
- **Entonces** el sistema verifica el estado del empleado, informando "Error: el empleado no posee el tiempo de antigüedad necesario (Un mes)".
 
> Escenario 3: Escenario fallido por licencia anterior vigente.  
- **Dado** Un empleado con una licencia anterior vigente.
- **Cuando** el empleado ingresa: el tipo de licencia telemedicina, la fecha de inicio de reposo 12/8/2025, la matrícula 138423, el diagnóstico "pierna rota" y "para el familiar enfermo", y presiona "Solicitar".
- **Entonces** el sistema verifica el estado del empleado, informando "Error: el empleado ya posee una licencia todavía vigente en el sistema".


---

ID: `Consultar Licencia`

Titulo: `Como` **`Administrador`** `quiero` **`Consultar las licencias solicitadas`** `para poder` **`Revisar el estado de un empleado`**

Reglas de negocio:
- Se podrá imprimir un solo informe por mes para cada empleado.

---

Criterios de aceptacion: `Consultar Licencia`

> Escenario 1: Escenario exitoso.  
- **Dado** Un CUIL 23-42993049-6 existente en el sistema y ninguna impresión de un informe en el mes.
- **Cuando** el administrador ingresa el CUIL 23-42993049-6 y un rango de fechas del 15/10/2026 al 15/12/2026 y presiona "Consultar".
- **Entonces** el sistema verifica los datos e imprime un informe de las licencias solicitadas.

> Escenario 2: Escenario fallido por CUIL inexistente.  
- **Dado** Un CUIL 27-24524565-2 inexistente en el sistema.
- **Cuando** el administrador ingresa el CUIL 27-24524565-2 y un rango de fechas del 15/10/2026 al 15/12/2026 y presiona "Consultar".
- **Entonces** el sistema verifica los datos e informa en pantalla "Error: No existe el número de CUIL ingresado".

> Escenario 3: Escenario fallido por reimpresión del informe mensual del empleado.  
- **Dado** Una impresión del informe en el mes.
- **Cuando** el administrador ingresa el CUIL 20-9824567-2 y un rango de fechas del 15/10/2026 al 15/12/2026 y presiona "Consultar".
- **Entonces** el sistema verifica los datos e informa en pantalla "Error: Ya se imprimió una copia del informe del empleado CUIL 20-9824567-2 en este mes".