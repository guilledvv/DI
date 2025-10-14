# Mi primer Hola Mundo con PySide6 — Guía paso a paso

##  Título y contexto

En este proyecto hice mi primera aplicación de escritorio con **PySide6**.  
Aprendí a crear un entorno virtual, instalar la librería y separar el archivo principal (`main.py`) de la clase de la ventana (`ventana.py`).  
Con esta guía, cualquier persona podrá repetir los pasos desde cero.

[Enlace a mi repositorio en GitHub](https://github.com/guilledvv/DI)  


---

##  Objetivos de aprendizaje

- Crear y activar un entorno virtual (venv).  
- Instalar dependencias con `pip`.  
- Ejecutar una ventana básica con PySide6.  
- Entender qué es `QApplication` y el ciclo de eventos (`app.exec()`).

---

##  Requisitos previos

- **Python:** versión 3.11  
- **Sistema operativo:** Windows, macOS o Linux  
- **Herramientas:** Git y un editor de código como VS Code

---

##  Creación y activación del entorno virtual

Primero creé mi entorno virtual.

### En Windows:
```bash
python -m venv venv
venv\Scripts\activate
```
## En macOS / Linux:
```bash

python3 -m venv venv
source venv/bin/activate
```
Verifiqué que el entorno estaba activo:

```
python --version
```
 Instalación de dependencias
Instalé la librería PySide6:
```
pip install PySide6
```
Después guardé las dependencias en un archivo:
```
pip freeze > requirements.txt
```

¿Qué es PySide6?
PySide6 es una librería que permite crear interfaces gráficas con Python usando la tecnología Qt.
Con ella puedo crear ventanas, botones, etiquetas y otros elementos visuales.
Documentación oficial de PySide6

Estructura del proyecto
```
proyecto-hola-mundo/
├─ src/
│  ├─ main.py          # punto de entrada
│  └─ ventana.py       # clase Ventana
├─ .gitignore
├─ requirements.txt
└─ README.md
```
Separé los archivos porque ventana.py tiene la clase de la interfaz y main.py solo inicia la aplicación.
Esto ayuda a mantener el código ordenado y fácil de ampliar.

## Código fuente (con explicación)
ventana.py
```
from PySide6.QtWidgets import QLabel, QWidget, QVBoxLayout
from PySide6.QtCore import Qt

class Ventana(QWidget):
    def __init__(self):
        super().__init__()

        # Configuración de la ventana
        self.setWindowTitle("Ventana de Ejemplo")
        self.resize(300, 200)

        # Crear un texto (etiqueta)
        self.etiqueta1 = QLabel("¡Hola, mundo!", self)
        self.etiqueta1.setAlignment(Qt.AlignCenter)

        # Layout (organiza los widgets verticalmente)
        layout = QVBoxLayout()
        layout.addWidget(self.etiqueta1)

        # Asigno el layout a la ventana
        self.setLayout(layout)
```
 Explicación:
En este archivo defino la clase Ventana, que hereda de QWidget.
Le pongo un título, un tamaño, y creo una etiqueta centrada con el texto “¡Hola, mundo!”.
Uso un QVBoxLayout para organizar el contenido dentro de la ventana.

 main.py
```
from PySide6.QtWidgets import QApplication
from ventana import Ventana
import sys

# Crear la aplicación (solo puede haber una)
app = QApplication(sys.argv)

# Crear una instancia de la ventana
ventana = Ventana()
ventana.show()

# Iniciar el bucle de eventos
app.exec()
```
 Explicación:
Este archivo es el punto de entrada del programa.
Primero creo una aplicación con QApplication, luego una ventana a partir de la clase Ventana, la muestro con .show(),
y finalmente inicio el bucle de eventos con app.exec(), que mantiene la app abierta hasta que la cierro.

 Ejecución y prueba
Para ejecutar el programa, entro en la carpeta src y uso:
```
python main.py
```
Al hacerlo, se abre una ventana con el título “Ventana de Ejemplo” y el texto “¡Hola, mundo!” en el centro.

(Aquí puedes poner una captura de pantalla si quieres)

Si cambio el texto del QLabel o el título de la ventana, los cambios se verán al ejecutar de nuevo.

 ## Problemas frecuentes y soluciones
Problema	Solución
El intérprete no usa el venv	Activa el entorno virtual antes de ejecutar
ModuleNotFoundError: PySide6	Revisa que PySide6 esté instalado en el entorno virtual
Error al ejecutar desde otra carpeta	Asegúrate de estar en src/ o usa rutas correctas

## Cierre y siguientes pasos
Para seguir aprendiendo, puedo añadir un botón y capturar el clic usando el sistema de señales y ranuras (signals and slots).
Esto sirve para conectar acciones del usuario con funciones en el código.

También puedo usar layouts (como QVBoxLayout o QHBoxLayout) para ordenar mejor los elementos en la ventana sin usar posiciones fijas.

## Checklist del proyecto
[x] Creé y activé el entorno virtual

[x] Instalé PySide6 y generé requirements.txt

[x] Separé main.py y ventana.py

[x] Incluí bloques de código con comentarios

[x] Expliqué QApplication, widgets y app.exec()

[x] Probé la app y documenté la ejecución

 Autor: [Guilledvv]
 Fecha: 14 Octubre 2025
