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

## Shadow DOM

- Oculta la complejidad de los *custom elements*
- Encapsula funcionalidad y estilos.
- Permite el *scope* del árbol de nodos

### Shady DOM

API de Polymer. Pseudo Shadow DOM
- Encapsula funcionalidad y estilos.
- Permite el *scope* del árbol de nodos
- Listo para producción

## Local DOM

Elementos HTML que estan dentro del componente.

## Light DOM 

Hijos del elemento.

### Manipulación del DOM

??????

# Propiedades

Se definen dentro del método *properties*

- type. Boolean, Date, Number, String, Array, Object
- value. Valor por defecto.
- observer. 

# Life cycle

El ciclo de vida de un componente en **Polymer** consta de 4 etapas, a saber:

* constructor
  Solo ocurre una sola vez. Se crea el componente, pero las propiedades y valores aun no estan inicializadas. El Local DOM (el DOM interno del componente) aun no se inicializa.

* ready
  Solo se ejecuta una sola vez. Valores y propiedades son inicialzados. El Local DOM se inicializa.

* connectedCallback
  Puede ser ejecutada multiples veces. El elemento se integra en el DOM.

* disconnectedCallback
  Puede ser ejecutada multiples veces. El elemento se quita del DOM.

* attributeChangedCallback
  Se ejecuta cuando algun atributo del componente cambia, se agrega, se remueve. Solamente trabaja con las propiedades definidas en el objeto dentro del método de *properties*.

# Estilos

Para agregar reglas css en el componente se usa el selector **:host** (LocalDOM)

Para agregar reglas css en el contenido del componente se usa el selector **:host ::slotted()** (LightDOM)

## CSS Custom properties

componente.html (Dentro del componente)
```` css
:host {
  background-color: var(--my-bg-color, #f00);
}
````

app.html (Fuera del componente)
```` css
:host {
  --my-bg-color: #f0f;
}
````

Permite exponer la parte personalizable del componente.

Permite personalizar componentes creados por otros.
  
Son aplicadas una sola vez en tiempo de creación

## Custom mixins

````
@apply(<nombre-del-mixin>)
````

componente.html (Dentro del componente)
```` css
#misReglas {
  @apply --mis-reglas;
}
````

app.html (Fuera del componente)
```` css
--mis-reglas {
  background-color: #f0f;
  color: #000;
  font-size: 16px;
}
````

Personaliza al 100% partes de nuestro componente.

## Actualizar estilos

```` javascript
this.customStyle['<custom-css-property>'] = '<valor>';
this.updateStyles();
````

Ya sea mediante una función o método mediante un evento.

# Eventos

Para manejar eventos desde los elementos del DOM se utiliza la sintaxis **on-<nombre-del-evento>** como atributo del elemento y cuyo valor será el método que se ejecutara para manejar el evento.

```` html
<button on-click="handleClick">click</button>
````

Todos los eventos son en *lowercase*.

El evento **on-tap** es mejor que **on-click**.