# SOLEMNE II — Pensamiento Computacional

# Proyecto: Sistema Bauhaus Interactivo

## Autor/a

Marcela Diaz

---

# Descripción objetiva

## ¿Qué es el proyecto?

Este proyecto consiste en un sistema visual dinámico e interactivo desarrollado en p5.js. El sistema genera una composición geométrica inspirada en la Bauhaus y el diseño generativo.

La composición cambia continuamente según el movimiento del mouse y la interacción del usuario.

---

## ¿Qué se ve en pantalla?

En pantalla aparece una grilla compuesta por figuras geométricas repetidas.

Las figuras incluyen:

* Círculos
* Cuadrados
* Triángulos
* Líneas diagonales

La composición utiliza colores primarios inspirados en la Bauhaus:

* Rojo
* Azul
* Amarillo

También utiliza líneas negras gruesas y una estructura modular basada en una retícula.

---

## ¿Qué inputs utiliza?

El sistema utiliza:

* mouseX
* mouseY
* click del mouse

---

## ¿Qué outputs genera?

El sistema genera:

* Cambio de tamaño de figuras
* Rotación de figuras
* Cambio de composición visual
* Variación geométrica
* Transformación continua del sistema

---

# Descripción conceptual

## Idea central del proyecto

La idea principal del proyecto es explorar cómo los principios visuales de la Bauhaus pueden transformarse en un sistema computacional dinámico.

El proyecto no busca copiar únicamente la estética Bauhaus, sino traducir sus principios de diseño a reglas programadas mediante código.

---

## Corriente o referente de diseño

El proyecto dialoga principalmente con:

* Bauhaus
* Diseño generativo
* Diseño modular

---

## Referentes visuales e históricos

### Bauhaus

Escuela de diseño moderno que utilizaba geometría simple, colores primarios, retículas y composiciones racionales.

### Wassily Kandinsky

Uso de geometría abstracta, círculos y relaciones visuales entre color y forma.

### Paul Klee

Exploración de sistemas visuales abstractos y estructuras geométricas.

### Diseño generativo

Uso de reglas y algoritmos para crear composiciones visuales variables.

---

## Principio de diseño explorado

El proyecto explora:

* Repetición
* Variación
* Modularidad
* Geometría básica
* Sistemas dinámicos
* Relación entre input y output

---

# Input / Output y sistema

## Reglas del sistema

El sistema funciona mediante una grilla de filas y columnas.

Cada celda contiene figuras geométricas que cambian según condiciones programadas.

El color cambia según operaciones matemáticas usando módulo (%).

Las figuras cambian según:

* Posición del mouse
* Click del usuario
* Condicionales
* Reglas de repetición

---

## Explicación de la interactividad

### mouseX

Controla el tamaño de las figuras.

Cuando el mouse se mueve hacia la derecha, las figuras aumentan de tamaño.

Cuando el mouse se mueve hacia la izquierda, las figuras disminuyen.

---

### mouseY

Controla la rotación de las figuras.

Mientras más abajo se mueve el mouse, mayor es la rotación.

---

### mousePressed()

Cada click cambia el sistema entre distintas composiciones geométricas.

---

## Qué datos entran

Los datos de entrada son:

* Posición horizontal del mouse
* Posición vertical del mouse
* Click del mouse

---

## Cómo se procesan

Los datos se procesan utilizando:

* Variables
* Función map()
* Condicionales if/else
* Bucles for
* Funciones propias
* Transformaciones geométricas

---

## Qué respuesta visual producen

Los datos generan:

* Cambios de escala
* Cambios de rotación
* Variación geométrica
* Transformaciones visuales continuas
* Cambios de composición

---

# Código sketch.js

```javascript
let cols = 8;
let rows = 8;
let shapeType = 0;

function setup() {
  createCanvas(500, 500);
  rectMode(CENTER);
}

function draw() {

  background(240, 235, 220);

  let w = width / cols;
  let h = height / rows;

  // bucle columnas
  for (let i = 0; i < cols; i++) {

    // bucle filas
    for (let j = 0; j < rows; j++) {

      let x = i * w;
      let y = j * h;

      let tam = map(mouseX, 0, width, 10, w);

      // llamar función propia
      dibujarFigura(x, y, w, h, tam, i, j);
    }
  }
}

// FUNCIÓN PROPIA
function dibujarFigura(x, y, w, h, tam, i, j) {

  // colores Bauhaus
  if ((i + j) % 3 === 0) {

    fill(255, 0, 0);

  } else if ((i + j) % 3 === 1) {

    fill(0, 0, 255);

  } else {

    fill(255, 204, 0);
  }

  stroke(0);
  strokeWeight(4);

  push();

  translate(x + w / 2, y + h / 2);

  // rotación según mouseY
  rotate(mouseY * 0.01);

  // composición cambia con click
  if (shapeType === 0) {

    if ((i + j) % 2 === 0) {

      ellipse(0, 0, tam * 0.7);

    } else {

      rect(0, 0, tam * 0.7, tam * 0.7);
    }

  } else {

    triangle(
      0, -tam / 2,
      -tam / 2, tam / 2,
      tam / 2, tam / 2
    );
  }

  pop();

  // líneas diagonales
  if (i % 2 === 0) {

    line(x, y, x + w, y + h);
  }
}

// interacción click
function mousePressed() {

  shapeType = 1 - shapeType;
}
```

---

# Diagrama de flujo

```text
INICIO
↓
setup()
↓
createCanvas()
↓
draw()
↓
leer mouseX y mouseY
↓
map(mouseX)
↓
for columnas
↓
for filas
↓
llamar dibujarFigura()
↓
if colores
↓
if formas
↓
rotate(mouseY)
↓
dibujar figuras
↓
mostrar output visual
↓
mousePressed()
↓
cambiar composición
↓
FIN
```

---

# Qué poner en GitHub

## Archivos mínimos

* sketch.js
* README.md
* imagen del diagrama
* archivo editable del diagrama
* imágenes de referentes

---

# Estructura recomendada del repositorio

```text
sistema-bauhaus/
│
├── sketch.js
├── README.md
├── diagrama.png
├── diagrama.fig
├── referentes/
├── imagenes/
```

---

# Qué poner en p5.js

Subir el código completo.

Luego copiar:

* Link editable
* Link para ejecutar

Y pegar ambos en el README.

---

# Ideas para imágenes del README

* Captura del sketch funcionando
* Referentes Bauhaus
* Diagrama de flujo
* Proceso de pruebas
* Bocetos

---

# Explicación corta para presentar

“Mi proyecto consiste en un sistema visual dinámico inspirado en la Bauhaus y el diseño generativo. Utilicé figuras geométricas básicas, colores primarios y una estructura modular basada en retículas. El sistema responde continuamente al movimiento del mouse mediante cambios de tamaño, rotación y composición. La idea fue traducir principios de diseño modernos a reglas computacionales usando p5.js.”
