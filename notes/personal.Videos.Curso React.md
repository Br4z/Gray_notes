---
id: cetjth3wbona2geofjabnw5
title: Curso React
desc: >-
  Title: Aprende React Desde Cero - Curso de React Con Proyectos
  URL: https://www.youtube.com/watch?v=6Jfk8ic3KVk&t
updated: 1689626536183
created: 1685840089151
---

## ¿Qué es React?

**Biblioteca** de JavaScript de codigo abierto diseñada para crear interfaces de usuario.

### ¿Qué es una biblioteca?

Conjunto de implementaciones o subprogramas que podemos usar en nuestro código.

## Conceptos básicos

### Componente

Parte de la interfaz de usuario independiente y reutilizable. Existen dos tipos.

#### Funcióneles

Función de JavaScript/ES6 que retorna un elemento de React (jsx). En sus características encontramos que:

- Debe retornar un elemento JSX.
- Debe comenzar con una letra mayúscula.
- Puede recibir valores si es necesario.

    Para lo cual existen los **props**, que son argumentos que pueden recibir un componente de React y solo pueden ser enviados de "padre a hijo".

```JSX
function Greeting(props) {
    return <h1> Hello {props.name}!</h1>;
}
```

#### Clase

Clase de ES6 (JavaScript moderno) que retorna un elemento JSX. En sus características encontramos que:

- Debe extender de `React.Component`.
- Debe tener un método `render()` que retorna un elemento de JSX (su estructura).
- Puede recibir valores si es necesario.

	> Accedemos a ellos de la forma `this.props.<prop name>`.

```JSX
class Greeting extends React.Component {
		reder() {
				return <h1> Hello {this.props.name}!</h1>;
		}
}
```

> Anteriormente, solo era posible trabajador con **estados** a través de ellos (en versiones de React anteriores a la 16.8).

##### Métodos

Función asociada a un componente que puede acceder y usar su estado.

###### Ciclo de vida

Son métodos especiales de React usados para realizar operaciones con componentes en momentos específicos de su vida en el DOOM.

### Estado

Representación en JavaScript del conjunto de propiedades de un componente y sus valores actuales.

> Con los **hooks** se hizo posible que los componentes funcionales trabajaran con estado (asignarlos y actualizarlos).

### Hook

Función especial (definida en React) que permite trabajar con estados en componentes funcionales y otros aspectos de React. **Sin** escribir componentes de clase.

> Esto nos permite escribir codigo mucho mas conciso y facil de entender.

### Event listener o event handler

Función en JavaScript que es ejecutada cuando ocurre un evento específico.

## JSX (JavaScript XML)

Extensión de React para la sintaxis de JavaScript. Nos permite describir en JavaScript como se verán (su estructura) los componentes usando una estructura similar a HTML.

## Elemento

Unidades más pequeñas en React. Definen lo que se ve en la pantalla (que es lo que haríamos con HTML).

> Un componente es una serie de elementos.

En JSX, los **elementos** HTML se representan con etiquetas en letras **minúsculas** a diferencia de los **componentes** definidos por el usuario que comienzan con una letra **mayúscula**. También podemos agregar (con JSX) **atributos** para especificar ciertas características.

## React DOM (Document Object Model)

Paquete que facilita la interacción y actualización del DOM en aplicaciones React.

> El DOM es la representación en el navegador de todos los elementos que conforman una página o aplicación web.

## Estructura

Al igual que en HTML, los elementos pueden ser **anidados** en JSX para formar estructuras más complejas.

## Crear una aplicación de React

1. `npx create-react-app <application name>`

## Exportaciones en React

### Por defecto

```JSX
// export default <component>;
// import <name> from <component path>

export default Testimony;

import Testimony from './components/Testimony';
```

### Nombrada

```JSX
// export <component definition>
// import {<component name>} from <component path>;

import {Testimony} from './components/Testimony';
```

## Sintaxis de desestructuración

Es una expresión de JavaScript que permite desempacar valores de arreglos o propiedades de objetos en distintas variables. Normalmente lo vamos a usar en las `props`.

```JSX
const user = {
	id: 42,
	is_verified: true
};

const {id, is_verified} = user;

console.log(id); // 42
console.log(is_verified); // true
```

## `useState`

Es un hook de React que nos permite añadir una variable de estado a nuestro componente.

```JSX
import {useState} from 'react';

function MyComponent() {
	const [age, setAge] = useState(28);
	const [name, setName] = useState('Taylor');
	const [all, setAll] = useState(() => craeteAll());
	// ...
}
```

Consiste en la declaración (como constante) de una arreglo de dos elementos, cuyo primer elemento corresponde a la variable en sí y el segundo al nombre de la función que la va a actualizar que va a ser igual a `useState(<initial variable value>)`.

```JSX
// const [variable, setVariable] = useState(<initial variable value>);
```
