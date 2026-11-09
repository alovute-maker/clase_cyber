# IA aplicada a la ciberseguridad · Cuadernos del laboratorio

Material de laboratorio del Máster en Ciberseguridad. Cada cuaderno es autónomo: la primera celda instala lo que falte y descarga los datos (NSL-KDD), así que funciona igual en Google Colab, en VS Code o en GitHub Codespaces.

```
ia-ciberseguridad/
├── notebooks/
│   ├── ia1_panorama.ipynb      Sesión 1 · Qué es la IA, ML y DL
│   └── ia2_datos.ipynb         Sesión 2 · Tipos de aprendizaje y preparación de datos
├── requirements.txt            Librerías del track
├── .devcontainer/              Configuración para GitHub Codespaces
└── .gitignore                  Excluye datos, entornos y ficheros generados
```

---

## Opción 1 · Google Colab (nada que instalar)

1. Entra en **https://colab.research.google.com** con tu cuenta de Google.
2. **Archivo › Subir cuaderno** y elige el `.ipynb` de la sesión. Si el material está en un repositorio de GitHub: **Archivo › Abrir cuaderno › GitHub** y pega la URL del repositorio.
3. Ejecuta la **celda de preparación** (`Mayús + Intro`). Debe mostrar «Entorno: Google Colab», los dos ficheros de datos y las versiones de las librerías.
4. Sigue las partes en orden.
5. **Guarda tu trabajo:** *Archivo › Guardar una copia en Drive*. Los ficheros del panel lateral (data/, utils.py, auth.log…) se borran al desconectar el entorno: al retomar, vuelve a ejecutar la celda de preparación y las celdas `%%writefile`.
6. **Para entregar:** *Entorno de ejecución › Reiniciar y ejecutar todo* y después *Archivo › Descargar › Descargar .ipynb*.

## Opción 2 · VS Code en tu equipo

1. **Python 3.11 o 3.12** desde https://www.python.org/downloads/. En Windows, marca **«Add python.exe to PATH»** en el instalador. Comprueba en una terminal:
   ```bash
   python --version        # macOS / Linux: python3 --version
   ```
2. **VS Code** desde https://code.visualstudio.com. En la vista de extensiones (`Ctrl+Mayús+X`) instala **Python** y **Jupyter**, ambas de Microsoft.
3. Descomprime esta carpeta y ábrela: **File › Open Folder… › ia-ciberseguridad**. Si VS Code pregunta si confías en los autores, responde que sí.
4. Crea el entorno virtual: `Ctrl+Mayús+P` › **Python: Create Environment** › **Venv** › tu Python › marca **requirements.txt**. VS Code crea `.venv` e instala las librerías.
   Alternativa en la terminal integrada (`Ctrl+ñ` o `Ctrl+``):
   ```bash
   python -m venv .venv
   .venv\Scripts\activate          # Windows
   source .venv/bin/activate       # macOS / Linux
   pip install -r requirements.txt
   ```
5. Abre `notebooks/ia1_panorama.ipynb` › **Select Kernel** (arriba a la derecha) › **Python Environments** › **.venv**.
6. Ejecuta la celda de preparación y sigue las partes en orden.

Herramientas de un entorno de desarrollo real:
- **Depurar una celda:** flecha junto a ▶ › *Debug Cell*; pon puntos de interrupción con clic a la izquierda del número de línea.
- **Variables:** botón *Variables* en la barra del cuaderno para inspeccionar DataFrames.
- **Terminal integrada:** `Ctrl+ñ` (o `Ctrl+``).
- **Control de versiones:** panel *Source Control* (`Ctrl+Mayús+G`) o en la terminal:
  ```bash
  git init
  git add .
  git commit -m "Sesión 1: laboratorio completado"
  ```

## Opción 3 · GitHub Codespaces (VS Code en la nube)

1. Crea una cuenta en **https://github.com**. Si eres estudiante, solicita **GitHub Education** (https://education.github.com) con tu correo académico: amplía las horas gratuitas de Codespaces.
2. Crea un repositorio vacío en **https://github.com/new** (por ejemplo `ia-ciberseguridad`, privado).
3. **uploading an existing file** › arrastra el **contenido** de esta carpeta, incluida `.devcontainer` › **Commit changes**. En macOS, `Cmd+Mayús+.` muestra las carpetas ocultas en el Finder.
4. En el repositorio: **Code › Codespaces › Create codespace on main**. La primera vez tarda unos minutos: instala Python, las extensiones y `requirements.txt`.
5. Abre `notebooks/ia1_panorama.ipynb` › **Select Kernel** › **Python Environments** › Python 3.12 y ejecuta la celda de preparación.
6. Al terminar: **commit y push** desde *Source Control* y detén el codespace en https://github.com/codespaces (*… › Stop codespace*) para no consumir horas.

---

## Problemas frecuentes

| Síntoma | Qué hacer |
|---|---|
| `ModuleNotFoundError: utils` | Ejecuta la celda `%%writefile utils.py` de la parte A (o la celda de preparación en la sesión 2). |
| En Colab han desaparecido los datos | Es normal al desconectar. Vuelve a ejecutar la celda de preparación. |
| Error al descargar los datos | Revisa la conexión o el proxy. Descarga `KDDTrain+.txt` y `KDDTest+.txt` de github.com/defcom17/NSL_KDD y ponlos en `data/`, junto al cuaderno. |
| VS Code no muestra `.venv` como kernel | `Ctrl+Mayús+P` › *Python: Select Interpreter* › `.venv`, y después *Developer: Reload Window*. |
| PowerShell no deja ejecutar `Activate.ps1` | Usa *Python: Create Environment* o ejecuta `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`. |
| `python` o `pip` no se reconocen (Windows) | Reinstala Python marcando *Add python.exe to PATH*, o usa `py` y `py -m pip`. |
| En Codespaces el kernel no arranca | Espera a que termine la configuración inicial (terminal *postCreateCommand*) y vuelve a elegir el kernel. |

Antes de entregar, reinicia siempre el kernel y ejecuta todo: un cuaderno que solo funciona con las celdas en otro orden no es reproducible.
