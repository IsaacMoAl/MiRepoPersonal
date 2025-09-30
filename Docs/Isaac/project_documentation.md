# Documentación del Proyecto — Aplicación Tkinter de Ventanas Múltiples

Este proyecto es un conjunto de ventanas gráficas desarrolladas en **Python** usando la librería **Tkinter** y sus widgets `ttk`.  
El objetivo es demostrar cómo crear ventanas secundarias con diferentes funcionalidades: mensajes de bienvenida, formularios, listas con CRUD básico, tablas desde CSV y gráficos en un lienzo.

---

## Índice
1. [Estructura del proyecto](#estructura-del-proyecto)
2. [Dependencias](#dependencias)
3. [Descripción de archivos](#descripción-de-archivos)
   - win_home.py
   - win_form.py
   - win_list.py
   - win_table.py (con `sample.csv`)
   - win_canvas.py
4. [Ejemplo de uso](#ejemplo-de-uso)
5. [Mejoras sugeridas](#mejoras-sugeridas)

---

## Estructura del proyecto

```
proyecto/
├── data/
│   └── sample.csv
├── win_home.py
├── win_form.py
├── win_list.py
├── win_table.py
├── win_canvas.py
└── README.md (este documento)
```

---

## Dependencias

- Python 3.8+
- Tkinter (incluido por defecto en la mayoría de distribuciones de Python)
- Librerías estándar: `csv`, `pathlib`

---

## Descripción de archivos

### `win_home.py`
Ventana simple de bienvenida.  
**Funciones principales:**
- `open_win_home(parent: tk.Tk)`  
  - Crea una ventana secundaria con:
    - Etiquetas de texto de bienvenida.
    - Botón **Mostrar mensaje** → muestra un `messagebox` de información.
    - Botón **Cerrar** → destruye la ventana.

Uso: Ideal como pantalla introductoria de la aplicación.

---

### `win_form.py`
Ventana con un formulario para capturar datos.  
**Funciones principales:**
- `open_win_form(parent: tk.Tk)`  
  - Contiene entradas de texto para:
    - Nombre
    - Edad
  - Función `validar_y_guardar()`:
    - Valida que el nombre no esté vacío.
    - Verifica que la edad sea un número entero.
    - Permite guardar los datos en un archivo `.txt` elegido por el usuario mediante `filedialog`.
    - Muestra un `messagebox` de confirmación.

Uso: Ejemplo de formulario con validación y persistencia en archivo.

---

### `win_list.py`
Ventana con **Listbox** para CRUD básico (agregar, eliminar, limpiar).  
**Funciones principales:**
- `open_win_list(parent: tk.Tk)`  
  - `agregar()`: añade un texto escrito en la caja de entrada al Listbox.
  - `eliminar()`: elimina el ítem seleccionado.
  - `limpiar()`: borra todos los ítems.

Uso: Ejemplo de manejo de listas dinámicas en Tkinter.

---

### `win_table.py`
Ventana con **Treeview** que muestra datos de un archivo CSV.  
**Funciones principales:**
- `open_win_table(parent: tk.Tk)`  
  - Configura un `Treeview` con columnas: `nombre`, `valor1`, `valor2`.
  - Carga los datos desde el archivo `data/sample.csv`.
  - Si el archivo no existe, muestra una advertencia.

Archivo de ejemplo `sample.csv`:

```csv
nombre,valor1,valor2
A,10,20
B,15,25
C,12,30
```

Uso: Ejemplo de lectura de CSV y despliegue tabular.

---

### `win_canvas.py`
Ventana con un **Canvas** de dibujo.  
**Funciones principales:**
- `open_win_canvas(parent: tk.Tk)`  
  - Dibuja ejemplos básicos:
    - Rectángulo
    - Óvalo
    - Línea
    - Texto

Uso: Ejemplo de gráficos 2D con Tkinter Canvas.

---

## Ejemplo de uso

Archivo principal (ejemplo `main.py`):

```python
import tkinter as tk
from win_home import open_win_home
from win_form import open_win_form
from win_list import open_win_list
from win_table import open_win_table
from win_canvas import open_win_canvas

def main():
    root = tk.Tk()
    root.title("Aplicación Tkinter Demo")
    root.geometry("300x250")

    tk.Button(root, text="Ventana Home", command=lambda: open_win_home(root)).pack(pady=5)
    tk.Button(root, text="Formulario", command=lambda: open_win_form(root)).pack(pady=5)
    tk.Button(root, text="Lista CRUD", command=lambda: open_win_list(root)).pack(pady=5)
    tk.Button(root, text="Tabla CSV", command=lambda: open_win_table(root)).pack(pady=5)
    tk.Button(root, text="Canvas", command=lambda: open_win_canvas(root)).pack(pady=5)

    root.mainloop()

if __name__ == "__main__":
    main()
```

---

## Mejoras sugeridas

1. Centralizar estilos (fuentes, tamaños, colores) para consistencia.
2. Crear un **menú principal** en lugar de botones independientes.
3. Manejar excepciones al abrir/guardar archivos.
4. Internacionalización (i18n) de mensajes.
5. Escribir pruebas unitarias básicas para funciones de validación (ej. edad).

---
