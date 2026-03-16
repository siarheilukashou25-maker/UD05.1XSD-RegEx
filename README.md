
**XML/XSD para los alumnos de una escuela e-learning**

  

*Expresión de email:*

  

> [a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}

  

Esta expresión permite validar un email y es muy simple. No he podido utilizar una expresión más avanzada porque el IDE, o más bien dicho XML, no me permite utilizar expresiones avanzadas como por ejemplo *RFC(2822)*

  

> /^([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x22([^\x0d\x22\x5c\x80-\xff]|\x5c[\x00-\x7f])*\x22)(\x2e([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x22([^\x0d\x22\x5c\x80-\xff]|\x5c[\x00-\x7f])*\x22))*\x40([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x5b([^\x0d\x5b-\x5d\x80-\xff]|\x5c[\x00-\x7f])*\x5d)(\x2e([^\x00-\x20\x22\x28\x29\x2c\x2e\x3a-\x3c\x3e\x40\x5b-\x5d\x7f-\xff]+|\x5b([^\x0d\x5b-\x5d\x80-\xff]|\x5c[\x00-\x7f])*\x5d))*$/

  

Así que he utilizado una más simple, que lo que hace es: permite introducir todos los símbolos alfanuméricos y más símbolos especiales como `_ . % + -`, después lo mismo pero después de un `@` y al final que sean mínimo dos letras para `.es`, `.com`, etc.

  

*Número de teléfono:*

  

> (\+?34)?(6[0-9]{2}|7[1-9][0-9]{1}|[89][0-9]{2})[0-9]{6}

  

Esta expresión permite validar un número de teléfono español. Al principio verifica el símbolo `+` que puede estar o no.

Después obliga a que el número empiece por `34`, que es el código español.

Después va un grupo de 3 números:

*Teléfono móvil:*

Empieza por `6` y después dos números cualesquiera más: `606`, `619`, `629`

Empieza por `7`, la segunda cifra puede ser de `1-9` (sin 0) y la última cualquier cifra: `717`, `734`, `752`

*Teléfono fijo:*

Empieza por `8` o `9` y dos cifras cualesquiera: `892`, `963`, `820`

Y por último 6 cifras cualesquiera: `701492`, `546278`, `290515`

  

*Código postal*

  

> (0[1-9]|[1-4][0-9]|5[0-2])[0-9]{3}

  

Esta expresión permite validar un código postal español.

Hay tres grupos:

-  `01-09`

-  `10-49`

-  `50-52`

Y por último 3 cifras cualesquiera.

  

*Nombre de usuario*

  

> [a-zA-Z0-9]|[_.-][a-zA-Z0-9]){1,18}[a-zA-Z0-9]

  

Esta expresión verifica el nombre de usuario: permite utilizar caracteres alfanuméricos y los símbolos `_ . -` para un *nickname*; debe empezar por una letra, después puede contener solo un símbolo `_ . -` seguido y tiene que terminar por una letra.

  

*Contraseña*

  

> \w{8,18}

  

Permite cualquier carácter alfanumérico y `_` de 8 a 18 veces. Es muy simple, pero por la misma razón que con el email no me permite usar una más fuerte, como por ejemplo esta:

  

    /^(?=.*\d)(?=.*[A-Z])(?=.*[a-z])(?=.*[^\w\d\s:])([^\s]){8,16}$/gm

  

Lo que hace es verificar una contraseña de 8 a 16 símbolos que tiene que tener como mínimo un número, una mayúscula y un símbolo especial.