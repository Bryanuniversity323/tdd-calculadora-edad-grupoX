# TDD - Calculadora de Edad

Proyecto listo para abrir en **Visual Studio Code**, desarrollado en **Python 3 + pytest** siguiendo el caso de TDD de la actividad.

## Estructura

```text
tdd-calculadora-edad/
├── src/
│   ├── __init__.py
│   └── edad.py
├── tests/
│   ├── __init__.py
│   └── test_edad.py
├── evidencias/
│   └── README.md
├── ACTIVIDAD_RESUELTA.md
├── requirements.txt
├── setup.bat
└── run_tests.bat
```

## Cómo abrirlo en VS Code

1. Descomprime el ZIP.
2. Abre Visual Studio Code.
3. Ve a **Archivo > Abrir carpeta**.
4. Selecciona `tdd-calculadora-edad`.
5. Abre una terminal en VS Code.
6. Instala pytest:

```bash
python -m pip install -r requirements.txt
```

7. Ejecuta las pruebas:

```bash
python -m pytest -v
```

Resultado esperado:

```text
7 passed
```

En Windows también puedes ejecutar `setup.bat` y luego `run_tests.bat`.

## Historial TDD

El proyecto incluye un repositorio Git con commits separados para las fases Red, Green y Refactor.

Para verlo:

```bash
git log --oneline --reverse
```

## Importante

Las capturas de pantalla deben ser tomadas por ti al ejecutar el proyecto, porque la actividad pide evidencias reales de las pruebas y del historial de commits.
