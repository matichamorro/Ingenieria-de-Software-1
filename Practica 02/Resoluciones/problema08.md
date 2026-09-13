# Practica 02
## Historias de usuario

### _Problema 8: Concursos_

ID: `Registrar Docente`

Titulo: `Como` **`Persona`** `quiero` **`Registrarme`** `para poder` **`Ingresar al sistema`**

Reglas de negocio:
- El mail debe ser único y será utilizado como nombre de usuario.
- Los DNI permitidos son aquellos menores a 55 millones y mayores a 12 millones.

---

Criterios de aceptacion: `Registrar Docente`

> Escenario 1: Escenario exitoso.  
- **Dado** un DNI 32.456.845 y un mail "pepopedro@gmail.com", ambos sin registrar.
- **Cuando** la persona ingresa: DNI 32.456.845, nombre "Pedro", apellido "Pedriga" y mail "pepopedro@gmail.com" y presiona "Registrarme".
- **Entonces** el sistema verifica los datos ingresados, crea la cuenta y manda al mail ingresado la contraseña asignada automáticamente.

> Escenario 2: Escenario fallido por mail repetido.  
- **Dado** un mail "pepopedro@gmail.com" ya registrado.
- **Cuando** la persona ingresa: DNI 32.456.845, nombre "Pedro", apellido "Pedriga" y mail "pepopedro@gmail.com" y presiona "Registrarme".
- **Entonces** el sistema verifica los datos ingresados, pero no crea una cuenta e informa en pantalla "Error: El mail ingresado ya fue registrado".

> Escenario 3: Escenario fallido por DNI repetido.  
- **Dado** un DNI 32.456.845 ya registrado.
- **Cuando** la persona ingresa: DNI 32.456.845, nombre "Pedro", apellido "Pedriga" y mail "pepopedro@gmail.com" y presiona "Registrarme".
- **Entonces** el sistema verifica los datos ingresados, pero no crea una cuenta e informa en pantalla "Error: El DNI ingresado ya fue registrado".

> Escenario 4: Escenario fallido por DNI fuera del rango permitido.  
- **Dado** un DNI 2.456.845 sin registrado.
- **Cuando** la persona ingresa: DNI 2.456.845, nombre "Pedro", apellido "Pedriga" y mail "pepopedro@gmail.com" y presiona "Registrarme".
- **Entonces** el sistema verifica los datos ingresados, pero no crea una cuenta e informa en pantalla "Error: El DNI ingresado se encuentra fuera del rango entre los 12 y los 55 millones".

---

ID: `Iniciar Sesión`

Titulo: `Como` **`Docente`** `quiero` **`Iniciar sesión`** `para poder` **`Entrar a mi cuenta para inscribirme`**

Reglas de negocio:
- El mail debe pertenecer a una cuenta existente

---

Criterios de aceptacion: `Iniciar Sesión`

> Escenario 1: Escenario exitoso.  
- **Dado** un mail "pepopedro@gmail.com" registrado con la contraseña "peponcio123".
- **Cuando** el docente ingresa: mail "pepopedro@gmail.com" y contraseña "peponcio123" y presiona "Iniciar sesión".
- **Entonces** el sistema redirige al usuario a la página de gestión de concursos.

> Escenario 2: Escenario fallido por mail no registrado.  
- **Dado** un mail "pepopedro@gmail.com" no registrado.
- **Cuando** el docente ingresa: mail "pepopedro@gmail.com" y contraseña "peponcio123" y presiona "Iniciar sesión".
- **Entonces** el sistema informa "Error: el mail o la contraseña no son correctos"

> Escenario 3: Escenario fallido por contraseña incorrecta.  
- **Dado** un mail "pepopedro@gmail.com" registrado con la contraseña "peponcio123".
- **Cuando** el docente ingresa: mail "pepopedro@gmail.com" y contraseña "pep000ooo" y presiona "Iniciar sesión".
- **Entonces** el sistema informa "Error: el mail o la contraseña no son correctos"


---

ID: `Inscribir a Concurso`

Titulo: `Como` **`Docente`** `quiero` **`Inscribirme al concurso`** `para poder` **`Aplicar a un puesto nuevo`**

Reglas de negocio:
- El docente no podrá inscribirse a más de 3 concursos.

---

Criterios de aceptacion: `Inscribir a Concurso`

> Escenario 1: Escenario exitoso.  
- **Dado** un docente inscripto a dos concursos anteriormente y una materia "Neuroanatomía" existente.  
- **Cuando** el docente ingresa la materia "Neuroanatomía".
- **Entonces** el sistema revisa los datos e imprime un comprobante, informando en pantalla "Inscripción completada correctamente".

> Escenario 2: Escenario fallido por materia inexistente.  
- **Dado** una materia "Neuroanatomía cuántica" que no existe.  
- **Cuando** el docente ingresa la materia "Neuroanatomía cuántica".
- **Entonces** el sistema revisa los datos e informa en pantalla "Error: La materia ingresada es inexistente".

> Escenario 3: Escenario fallido por docente con más de tres concursos inscriptos.  
- **Dado** un docente inscripto a tres concursos anteriormente
- **Cuando** el docente ingresa la materia "Neuroanatomía".
- **Entonces** el sistema revisa los datos e informa en pantalla "Error: No puede inscribirse a más concursos, actualmente está inscripto a tres". 


---

ID: `Imprimir Listado`

Titulo: `Como` **`Jefe del área de concursos`** `quiero` **`Imprimir un listado con los inscriptos`** `para poder` **`Enviar dicho listado al secretario administrativo`**

Reglas de negocio:
- El listado de inscriptos debe seguir el formato del SIU Guaraní

---

Criterios de aceptacion: `Imprimir Listado`

> Escenario 1: Escenario exitoso.  
- **Dado** la materia "Historia 2" con 15 docentes inscriptos.
- **Cuando** el jefe ingresa la materia "Historia 2" y presiona "Imprimir listado".
- **Entonces** el sistema imprime un listado de la lista de los 15 docentes inscriptos.

> Escenario 2: Escenario fallido por falta de inscriptos.  
- **Dado** la materia "Historia 1" que no tiene docentes inscriptos.
- **Cuando** el jefe ingresa la materia "Historia 1" y presiona "Imprimir listado".
- **Entonces** el sistema no genera ningún listado e imprime en pantalla "La materia ingresada no posee ningún docente inscripto".

---

ID: `Cerrar Sesión`

Titulo: `Como` **`Docente`** `quiero` **`Registrarme`** `para poder` **`Ingresar al sistema`**

Reglas de negocio:
- El mail debe pertenecer a una cuenta existente

---

Criterios de aceptacion: `Cerrar Sesión`

> Escenario 1: Escenario exitoso.  
- **Dado** un docente que ha iniciado sesión anteriormente.
- **Cuando** el docente presiona "Cerrar sesión".
- **Entonces** el sistema cierra la sesión y redirige al usuario a la página de inicio de sesión.

