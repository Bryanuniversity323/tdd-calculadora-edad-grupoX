# ACTIVIDAD RESUELTA – DESARROLLO GUIADO POR PRUEBAS (TDD)

## Datos

- Integrante: Bryan Niquen Surita
- Lenguaje y framework: Python 3 + pytest
- Repositorio: completar con el enlace de GitHub
- Sección / Grupo: completar
- Fecha: completar

## Bitácora de ciclos

| Ciclo | Prueba escrita | Red: ¿por qué falló? | Green: ¿qué cambiaste? | Refactor realizado |
|---|---|---|---|---|
| 1 | `test_edad_cuando_ya_cumplio_anios_este_anio` | La función `calcular_edad` aún no existía. | Se creó `calcular_edad` con la resta entre el año actual y el año de nacimiento. | No fue necesario. |
| 2 | `test_edad_cuando_aun_no_cumple_anios_este_anio` y `test_edad_el_dia_del_cumpleanios` | La implementación inicial solo restaba años y no verificaba si el cumpleaños ya había ocurrido. | Se agregó la comparación de mes y día para restar un año cuando el cumpleaños aún no llega. | Se mantuvo la lógica simple y legible. |
| 3 | `test_fecha_nacimiento_futura_lanza_excepcion` | El programa devolvía una edad inválida en vez de lanzar una excepción. | Se añadió la validación de fecha futura y el `ValueError` solicitado. | Luego la validación se extrajo a una función propia. |
| 4 | Tres pruebas para nacimiento el 29 de febrero | Las pruebas no fallaron porque la comparación de `(mes, día)` creada en el ciclo 2 ya cubría correctamente el caso. | No fue necesario cambiar el comportamiento. | Las pruebas quedaron como protección ante cambios futuros. |
| 5 | — | — | — | Se extrajo `validar_fecha_nacimiento`, se extrajo `ya_cumplio_anios` y se definió una constante para el mensaje de error. |

## Preguntas de reflexión

### 1. ¿Por qué la función recibe la fecha actual como parámetro?

Recibe la fecha actual como parámetro para que las pruebas sean repetibles y deterministas. Si la función utilizara directamente `date.today()`, el resultado podría cambiar con el paso del tiempo y una prueba que hoy funciona podría fallar dentro de un año. Al usar una fecha fija, el resultado siempre es el mismo.

### 2. En el ciclo 1 el código era incorrecto y la prueba pasaba. ¿Qué enseña esto?

Demuestra que una sola prueba no garantiza que toda la funcionalidad sea correcta. La primera prueba solo cubría el caso de una persona que ya había cumplido años. Por ello es necesario probar diferentes escenarios normales, límites y de error.

### 3. ¿Las pruebas del ciclo 4 fallaron?

No. Las pruebas del ciclo 4 pasaron sin modificar la lógica porque la comparación entre mes y día implementada previamente ya hacía que una persona nacida el 29 de febrero mantuviera su edad hasta el 28 de febrero y la incrementara desde el 1 de marzo en un año no bisiesto. Las nuevas pruebas siguen siendo importantes porque dejan ese comportamiento protegido.

### 4. Clases de equivalencia y valores límite

Clases de equivalencia identificadas:
- Fecha de nacimiento válida: anterior o igual a la fecha actual.
- Fecha de nacimiento inválida: posterior a la fecha actual.
- Cumpleaños ya ocurrido.
- Cumpleaños aún pendiente.
- Nacimiento el 29 de febrero.

Valores límite principales:
- Día anterior al cumpleaños.
- Día exacto del cumpleaños.
- Día posterior al cumpleaños.
- 28 de febrero, 29 de febrero y 1 de marzo para el caso bisiesto.

### 5. Ventaja y desventaja de TDD

Ventaja: permite detectar errores desde etapas tempranas y ofrece una red de seguridad para refactorizar el código.

Desventaja: requiere más disciplina y tiempo al inicio porque cada comportamiento debe comenzar con una prueba antes de escribir el código de producción.

## Resultado final

El proyecto contiene siete pruebas que cubren RF1, RF2, RF3 y RF4. Al ejecutar:

```bash
python -m pytest -v
```

deben pasar las siete pruebas.
