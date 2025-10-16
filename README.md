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

# Programación Python (Avanzado)-Generación de Hostnames 

Este repositorio contiene la practica de Programación Python (avanzado). El objetivo es generar un dataset de hostnames, construir un DataFrame de Pandas y producir visualizaciones con Matplotlib siguiendo las reglas, funciones y entregables definidos en la guía de la práctica.

🎯 Objetivos 

Generar hostnames aleatorios cumpliendo reglas de formato y proporciones por SO, entorno y país.

Construir un DataFrame a partir de dichos hostnames.

Exportar el DataFrame a CSV y validarlo con una lectura posterior.

Crear gráficas (barras, barras horizontales y tarta) para responder a preguntas de distribución.

🔤 Reglas del hostname

Longitud: 8 caracteres alfanuméricos (letras mayúsculas).

1er carácter = SO: L (Linux), S (Solaris), A (AIX), H (HP-UX).

Proporciones: Linux 40%, Solaris 30%, AIX 20%, HP-UX 10%.

2º carácter = Entorno: D (Development), I (Integration), T (Testing), S (Staging), P (Production).

Proporciones: 10%, 10%, 25%, 25%, 30% respectivamente.

3º–5º carácter = País: NOR, FRA, ITA, ESP, DEU, IRL.

Proporciones: NOR 6%, FRA 9%, ITA 16%, ESP 16%, DEU 23%, IRL 30%.

6º–8º carácter = número de nodo incremental 001–999 por combinación (SO, entorno, país).

🧩 Funciones implementadas

set_hostnames(number_of_hosts: int) -> list[str]
Genera la lista de hostnames cumpliendo formato y proporciones. Gestiona el contador de nodo por clave (SO-ENV-PAÍS).

get_os(hostname: str) -> str
Devuelve Linux|Solaris|AIX|HP-UX según 1ª letra; en caso no válido, Unknow.

get_enviroment(hostname: str) -> str
Devuelve Development|Integration|Testing|Staging|Production según 2ª letra; si no corresponde, Unknow.

get_country(hostname: str) -> str
Devuelve Norway|Germany|Italy|Spain|Ireland|France según posiciones 3–5; si no corresponde, Unknow.

set_dataframe(count: int) -> None
Declara global df, construye dataset (lista de dicts) con campos:
hostname, os, enviroment, country, node, y asigna df (Pandas).

📦 Dependencias

Python 3.9+, Jupyter Notebook/Colab.

pandas, matplotlib (y opcionalmente seaborn).
Instalación rápida:

pip install pandas matplotlib seaborn


🧪 Esquema de datos (DataFrame df)

hostname (str), p. ej. LDIRL003

os (str), p. ej. Linux

enviroment (str), p. ej. Development

country (str), p. ej. Ireland

node (int), p. ej. 3


📊 Visualizaciones requeridas

Country vs Enviroment
Agrupar por country y enviroment, usar unstack y plot(kind='bar').

Figura 2×2 (subplots)

Sup. izquierda: Type of OS grouped by country → groupby(['country','os']).size().unstack().plot(kind='barh').

Sup. derecha: Total Operating Systems → df['os'].groupby(df['os']).size().plot(kind='pie', labels=..., legend=True) incluyendo número y porcentaje por SO.

Inf. izquierda: Total hosts by country → df['country'].value_counts() en barras horizontales, ejes etiquetados (x: Number of hosts, y: Country), anotar el total al final de cada barra y ajustar xlim al máximo + 100.

Inf. derecha: Hosts by country grouped by enviroment → groupby(['country','enviroment']).size().unstack(0).plot(kind='bar') con etiqueta del eje y Number of hosts.

Ajustar espacios con fig.tight_layout().


🧱 Buenas prácticas

Validar entradas y manejar casos no estándar devolviendo Unknow en funciones de mapeo.

Comentar el código y mantener nombres descriptivos.

Fijar semillas aleatorias si se necesita reproducibilidad de proporciones.



