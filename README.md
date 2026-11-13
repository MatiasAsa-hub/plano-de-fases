# Plano de Fases

Graficador interactivo de sistemas dinámicos autónomos en 2D:

```
ẋ = f(x, y; parámetros)
ẏ = g(x, y; parámetros)
```

**Usalo online:** https://matiasasa-hub.github.io/plano-de-fases/

Es una sola página web (`index.html`): también se puede descargar y abrir en el navegador, sin instalar nada.

## Qué hace

- **Retrato de fases**: muestra el campo como líneas de flujo o como flechas. Con un clic lanzás una trayectoria (también se puede integrar hacia atrás). Arrastrando movés el plano y con la rueda hacés zoom.
- **Nulclinas** ẋ = 0 y ẏ = 0, que se pueden activar y desactivar.
- **Puntos fijos**: los busca dentro de la ventana con Newton amortiguado y los clasifica como nodo, foco, silla, estrella, centro o no hiperbólico. Dibuja los autovectores y las separatrices (variedades estable e inestable) de las sillas.
- **Linealización**: muestra el jacobiano simbólico J(x, y) y su valor en el punto, el sistema lineal en u = x − x*, v = y − y*, la traza τ, el determinante Δ, τ² − 4Δ, los autovalores y los autovectores, junto con un mini retrato del sistema lineal.
- **Parámetros**: cualquier nombre que no sea `x` o `y` (`r`, `mu`, `a`…) se vuelve un parámetro con su slider y su rango.
- **Diagrama de bifurcación**: muestra las ramas de puntos fijos según el parámetro, coloreadas por estabilidad. Detecta bifurcaciones silla-nodo, transcríticas, de horquilla y de Hopf, y puede simular los ciclos límite estables.

## Sintaxis

Variables `x`, `y`; operadores `+ - * / ^`; funciones `sin cos tan exp log ln sqrt abs tanh sinh cosh atan`…; constantes `pi`, `e`.

Ejemplo (Hopf supercrítica):

```
ẋ = mu*x - y - x*(x^2 + y^2)
ẏ = x + mu*y - y*(x^2 + y^2)
```

## Ejemplos incluidos

Competencia de Lotka–Volterra, silla-nodo, transcrítica, horquilla supercrítica y subcrítica, Hopf supercrítica, Van der Pol, péndulo amortiguado, glucólisis de Sel'kov y un sistema desacoplado ẋ = h(x), ẏ = j(y).

## Limitaciones

- Los puntos fijos y las bifurcaciones solo se buscan dentro de la ventana visible.
- La detección de bifurcaciones es numérica, sobre una grilla del parámetro: el valor es aproximado y la clasificación es la más probable.
- Los ciclos límite se encuentran por simulación, así que solo aparecen los estables.

## Tecnología

HTML, CSS y JavaScript sin dependencias de compilación. Usa [math.js](https://mathjs.org/) desde CDN para leer las expresiones y derivarlas en forma simbólica.
