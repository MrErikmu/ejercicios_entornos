# Prueba completa caja negra 
## Campos de formulario: 
- Nombre completo 2/100 caracteres 
- Fecha Nacimiento solo año-> 1900 
- Calificación de 0.00 a 10.00
- Email  
- DNI Español
---
### Campo Nombre

| Aspecto | Análisis | Resultado |
|:---------:|:----------:|:-----------:|
| **Tipo de dato** | Texto String | Solo Texto |
| **Longitud** | <2 y >100 | 3-99 |
| **Obligatoriedad** | Obligatorio | No Puede estar vacío |
| **Valores inválidos** | Numeros, símbolos, longitud incorrecta | Error de validación |

**Particiones resultantes:**

| ID | Partición | Valores de Prueba | Resultado Esperado |
|:----:|:-----------:|:-------------------:|:-------------------:|
| T1 | Vacío | `""` | Invalido (obligatorio) |
| T2 | Longitud corta(2) | `"Lo"`  | Inválido |
| T3 | Longitud correcta (3-99) | `"Juan"` | Válido |
| T4 | Longitud larga (100) | `"aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"` | Invalido |
| T5 | Null |  | Inválido |
| T6 | Con Numeros | `"Juan22"` | Inválido |
| T7 | Con símbolos | `"Juan$$"` | Inválido |
| T8 | Solo espacios | `"       "` | Inválido |
---
### Campo Fecha de Nacimiento

| Aspecto | Análisis | Resultado |
|:---------:|:----------:|:-----------:|
| **Tipo de dato** | Int Numero | Solo Digitos |
| **Longitud** | Exactamente 4 Digitos |
| **Obligatoriedad** | Obligatorio | No Puede estar vacío |
| **Valores inválidos** | Letras, símbolos, longitud incorrecta,Negativo,  | Error de validación |

**Particiones resultantes:**

| ID | Partición | Valores de Prueba | Resultado Esperado |
|:----:|:-----------:|:-------------------:|:-------------------:|
| T1 | Vacío | `""` | Invalido (obligatorio) |
| T2 | NULL | | Inválido |
| T3 | Longitud correcta (4) | `"1998"` | Válido |
| T4 | Longitud larga (100) | `"11111"` | Invalido |
| T5 | Longitud Corta | `"111"` | Inválido |
| T6 | Con Letras | `"22aa"` | Inválido |
| T7 | Con símbolos | `"--22"` | Inválido |
| T8 | Solo espacios | `"       "` | Inválido |
| T9 | No Entero | `"11.5"` | Inválido |
| T10 | No Numero | `"aaaa"` | Inválido |
---
### Campo Calificacion

| Aspecto | Análisis | Resultado |
|:---------:|:----------:|:-----------:|
| **Tipo de dato** |  Numero con 1 decimal| Solo Digitos |
| **Longitud** | Exactamente 2 Digitos |
| **Obligatoriedad** | Obligatorio | No Puede estar vacío |
| **Valores inválidos** | Letras, símbolos, longitud incorrecta,Negativo, <10  | Error de validación |

**Particiones resultantes:**

| ID | Partición | Valores de Prueba | Resultado Esperado |
|:----:|:-----------:|:-------------------:|:-------------------:|
| T1 | Vacío | `""` | Invalido (obligatorio) |
| T2 | NULL | | Inválido |
| T3 | Longitud correcta (2) | `"9.5"` | Válido |
| T4 | Longitud larga (3) | `"100"` | Invalido |
| T5 | Con Letras | `"9a"` | Inválido |
| T6 | Con Simbolos | `"9~"` | Inválido |
| T7 | Solo Espacios | `"  "` | Inválido |
| T8 | Fuera de Rango Inferior | `"-2"` | Inválido |
| T9 | Fuera de Rango Superior | `"11.5"` | Inválido |
| T10 | No Numero | `"aaaa"` | Inválido |
| T11 | Numero no decimal | `"6"` | Inválido |
---

### Campo Email

| Aspecto | Análisis | Resultado |
|:---------:|:----------:|:-----------:|
| **Tipo de dato** | Texto con numeros y restricciones de caracteres | Texto y Digitos |
| **Longitud** | Maximo 320 Caracteres |
| **Obligatoriedad** | No Obligatorio | Puede estar vacío |
| **Valores inválidos** | ampersand (&), signo igual (=), guion bajo (_), apóstrofo ('), guion (-), signo más (+), coma (,), corchetes angulares (<,>)., longitud incorrecta, Varios puntos seguidos, empezar con punto, terminar con punto, ausencia de domino superior, estructura incorrecta | Error de validación |

**Particiones resultantes:**

| ID | Partición | Valores de Prueba | Resultado Esperado |
|:----:|:-----------:|:-------------------:|:-------------------:|
| T1 | Vacío | `""` | Valido |
| T2 | NULL | | Valido |
| T3 | Longitud correcta | `"correo@correo.com"` | Válido |
| T4 | Longitud larga | `"asdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklp@asdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklpasdfghjklp"` | Invalido |
| T5 | Con & | `"correo&c@correo.com"` | Inválido |
| T6 | Con =  | `"correo=c@correo.com"` | Inválido |
| T7 | Con _ | `"correo_c@correo.com"` | Inválido |
| T8 | Con ' | `"correo'c@correo.com"` | Inválido |
| T9 | Con - | `"correo-c@correo.com"` | Inválido |
| T10 | Con +  | `"correo+c@correo.com"` | Inválido |
| T10 | Con , | `"correo,c@correo.com"` | Inválido |
| T11 | Con <> | `"correo<c@correo.com"` | Inválido |
| T12 | Con multiples puntos seguidos  | `"correo....c@correo.com"` | Inválido |
| T13 | Terminado en.  | `"correo@correo.com."` | Inválido |
| T14 | Sin Dominio superior  | `"correo@correo"` | Inválido |
| T15 | Sin @  | `"correocorreo.com"` | Inválido |
| T16 | Sin parte local  | `"@correo.com"` | Inválido |
| T17 | Sin parte del dominio  | `"correo@.com"` | Inválido |
---

### Campo DNI 

| Aspecto | Análisis | Resultado |
|:---------:|:----------:|:-----------:|
| **Tipo de dato** | Texto con numero| Texto y Digito |
| **Longitud** | 8 Digitos y 1 Letra |
| **Obligatoriedad** | Obligatorio | No Puede estar vacío |
| **Valores inválidos** | Null, Vacio, Letra incorrecta, letra primero, mas de 8 digitos, solo espacios, | Error de validación | 

****Particiones resultantes:**

| ID | Partición | Valores de Prueba | Resultado Esperado |
|:----:|:-----------:|:-------------------:|:-------------------:|
| T1 | Vacío | `""` | Invalido (obligatorio) |
| T2 | NULL | | Invalido |
| T3 | Solo espacios | `"          "` | Invalido  |
| T4 | Longitud larga | `"483586308Q"`  | Invalido |
| T5 |Longitud Corta | `"4835863Q"`  | Invalido |
| T6 | Letra Primero  |`"Q4835863"`  | Invalido |
| T7 | Letra Incorrecta | `"49358632P"` | Inválido |
| T8 | Sin Letra | `"49358632"` | Inválido |
| T9 | Sin Digitos | `" P"` | Inválido |
---
