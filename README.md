# Programación Python (Básico)-Juego de Adivinanzas

Proyecto de práctica de Python (básico). El objetivo es desarrollar un juego de adivinanza con menú principal, selección de dificultad, almacenamiento de resultados en Excel, y módulos de resumen y gráficas de partidas.

🎯 Objetivos de aprendizaje

Estructurar un programa con menús y validaciones reutilizables.

Aplicar aleatoriedad (número a adivinar 0–1000) y control de intentos.

Persistir datos en una hoja de cálculo y generar resúmenes + gráficas por nivel.

Documentar el código con comentarios claros (impacta en la puntuación).

🗂️ Estructura del repo
├─ Juego de Adivinanza Python Básico.ipynb   # cuaderno principal (requerido por la práctica)
├─ data/
│  └─ partidas.xlsx                          # hoja de cálculo con resultados (se crea/usa)
├─ figures/                                  # gráficas generadas (opcional)
└─ README.md


🧩 Funcionalidad
Menú principal

Al iniciar, se muestra un menú con tres opciones:

Jugar

Mostrar resumen partidas

Mostrar gráficas partidas
La opción elegida se valida mediante una función reutilizable.

Dificultad e intentos

Antes de jugar, se elige nivel:

Fácil → 15 intentos

Medio → 10 intentos

Difícil → 5 intentos
Se valida la selección con la misma función de validación.

Mecánica del juego

Se genera un número aleatorio entre 0 y 1000.

En cada intento se informa cuántos intentos quedan.

Si acierta → se felicita y termina la partida.

Si falla → se indica si el número buscado es mayor o menor.

Persistencia de resultados (Excel)

Al finalizar (acierto o agotamiento de intentos), se guarda el resultado en una hoja de cálculo partidas.xlsx, actualizando la celda/fila correspondiente. La hoja se prepara previamente con información inicial (o se crea si no existe).

Resumen de partidas

Se lee la hoja de cálculo con una función lectora y se muestra un resumen del tipo:

RESUMEN DE PARTIDAS
-----------------------------
          VICTORIAS  DERROTAS
FÁCIL:        x         y
MEDIO:        x         y
DIFÍCIL:      x         y


Gráficas

A partir de la misma función lectora, se muestran una o varias gráficas por nivel con las victorias/derrotas (o métricas equivalentes).

🧪 Requisitos y criterios de evaluación (resumen)

Menú principal con 3 opciones (+0,5).

Validación genérica de opciones (+1).

Dificultades 15/10/5 intentos (+3 si incluye nivel + resumen + gráfico).


🔧 Requisitos técnicos

Python 3.9+

Jupyter Notebook

Paquetes sugeridos: pandas, openpyxl (para Excel), matplotlib (para gráficas), numpy (opcional), random (estándar).

Instalación rápida:

pip install pandas openpyxl matplotlib

▶️ Cómo ejecutar

Abre Juego de Adivinanza Python Básico.ipynb en Jupyter.

Ejecuta todas las celdas en orden.

Sigue el menú interactivo en la salida del notebook.

Consulta data/partidas.xlsx para ver los registros y figures/ para las gráficas (si se guardan).

📊 Estructura sugerida de partidas.xlsx

Mínimo, una tabla con columnas como:

fecha, nivel (facil|medio|dificil), resultado (victoria|derrota), intentos_usados, numero_objetivo.

La práctica indica preparar la hoja con información inicial y actualizar la celda/fila al finalizar cada partida.

🧱 Diseño y buenas prácticas

Funciones reutilizables para validación de entradas y lectura de Excel.

Mensajes claros al usuario (intentos restantes, mayor/menor, errores de opción).

Comentarios en el código explicando la lógica de cada bloque/celda.

🚀 Próximas mejoras (opcional)

Guardar también tiempo de partida.

Añadir modo infinito con ranking de intentos.

Exportar gráficas a PNG/PDF automáticamente.

