# Polymer

Filosofía: Utilizar la plataforma, aprovechar las API's que ya ofrecen los navegadores de forma nativa y estándar. Se basa en 4 tecnólogias:
- TEMPLATES
- CUSTOM ELEMENTS
- SHADOW DOM
- HTML IMPORTS
- SCRIPT TYPE MODULE ES6

Simplifica la sintaxis para crear **Web Components**.

# Web Components
Especificaciones, estándares abiertos que los navegadores implementan para facilitar el desarrollo de nuevos elementos que extienden la web.

Herramientas para crear *etiquetas* nuevas.

## Componentes nativos

Los componentes nativos se crean a partir de una clase de ES6 y extienden del elemento HTMLElement. El cual es el elemento básico y contiene todo el código para que cualquier elemento funcione.

```` javascript
class MiComponente extends HTMLElement {
  ...
}
````
Para registrar el elemento se usa el método define, como se muestra a continuación:

```` javascript
customElements.define('mi-componente', MiComponente);
````
El cual asocia un nombre de componente (la etiqueta del componente) con una clase de ES6.

Y para utilizarlo, lo hacemos como si se tratara de cualquier elemento HTML como sigue:

```` html
<mi-componente></mi-componente>
````
El primer método que se ejecuta es el constructor.

El método **attachShadow** permite añadir el *Shadow DOM* (árbol de componentes y etiquetas que puede tener dentro un componente y que esta encapsulado, permite crear contenido que puede o no estar accesible desde fuera del componente).

Componentes encapsulados desde el **shadow root**
### TEMPLATE

La etiqueta **template** no *'aparece'*. Para usarlo dentro de un *custom element*, le asignamos un *id* y accedemos a su contenido y lo volcamos dentro del *custom element* mediante la propiedad **innerHTML** de los elementos.
