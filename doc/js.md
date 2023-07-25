# JavaScript

* Es un lenguaje de programación interpretado, no compilado.
* El código puede ser interpretado:
  * **En el cliente**: computadora del usuario
  * **En el servidor**: entorno de desarrollo Node.js
* Nace en 1995. Creador: Brendan Eich.
* Utilizado para generar scripts para la web.
* Valida datos en la máquina del cliente antes de enviarlos al servidor.
* Es un lenguaje multiparadigma, basada en prototipos (estilo de POO), dinámico, soporta estilos de programación funcional. OO e imperativa.
* Es case sensitive, es decir, es capaz de distinguir mayúsculas y minúsculas.
* Las diferentes versiones de JavaScript han sido finalmente integradas en un estándar denominado ECMAScript-262. Las versiones actuales de los navegadores soportan este estándar.

## Usos

* Crear animaciones
* Validar formularios
* Realizar acciones o eventos
* Insertar código HTML o CSS
* etc.

## Integración con HTML

* Hay dos sitios dentro de una página donde se puede situar código:
  * Dentro de la etiqueta \<head>: se suele utilizar normalmente para cargar archivos externos.
  * Dentro de la etiqueta \<body>: aquí se coloca habitualmente el código que va a realizar acciones sobre la página. Luego se verá que existen algunas restricciones.

    ```html
    <html>
    <head>
        <script type="text/javascript" src="mi_code.js"></script>
    </head>
    <body>
        <script>
            // Comentario en linea
            /* 
               Comentario
               multilinea
            */
            alert("Hola mundo en ventana")        // muestra ventana de aviso
            console.log("Hola mundo en consola")  // muestra en consola (F12)
        </script>
    </body>
    </html>
    ```

## Sintaxis

![Sintaxis](img/js-sintaxis.jpg)

## Variables

* Una variable es un lugar donde guardar un valor que voy a necesitar más adelante.
* Nombre de variable: ($|_|L)(L|D|$|_)*
  * Los nombres distinguen entre mayúsculas y minúsculas (x es distinto de X)
  * No pueden ser palabras reservadas del lenguaje.
* No tipado: no es necesario definir el tipo de una variable al declararla.

```javascript
var miEdad        // Declaración explícita sin valor
var miEdad = 26   // Declaración explícita con valor
miEdad            // Declaración implícita sin valor (ERROR)
miEdad = 26       // Declaración implícita con valor

const PI = 3.14
const VALOR_MAXIMO = 256

var edad
edad = 26
edad = "veintiseis"
```

## Tipos de datos

```javascript
var year = 2022       // NUMBER
var name = "Pablo"    // STRING
var isPremium = true  // BOOLEAN
var algo              // UNDEFINED
```

## Operadores

| **Nombre** | **Operador/es** | **Ejemplos** |
| -- | -- | -- |
| Asignación| = | miDato = 5 |
| Aritméticos | +, -, ++, --, \*, /, %, +=, -=, *=, /=, %= | miDato++ |
| Cadenas | + | miDato = "Hola " + "mundo" |
| Lógicos | !, &&, \|\| | miDato = true && false |
| Relacionales | ==, !=, >, >=, <, <= | miDato = 5 > 3 |
| Estricta (tipo y valor) | ===, !== | 5 === "5" //false |
| Condicional | op1?op2:op3 | mayoria = (edad >= 18)? "si" : "no" |
| Tipo de dato | typeof | typeof(5.9)  //"number" |
| Punto | . | miObjeto.propiedad |
| Corchetes | [] | miObjeto[propiedad] |
| Creación | new | new miObjeto |
| Borrado | delete | delete miObjeto.propiedad |
| Existencia | in | propiedad in miObjeto |
| instanceof | instanceof | miCoche instanceof objetoCoche |
| actual | this | this.propiedad |

## Estructuras de control

* **Condicionales**: un condicional es una sentencia que me permite ejecutar códigos alternativos en función de una condición dada.

```javascript
var edad = 14
if (edad >= 18) {
    console.log('Mayor de edad')
} else {
    console.log('Menor de edad')
}

var semaforo = "gris"
switch (semaforo) {
    case "rojo": console.log('Stop'); break
    case "amarillo": console.log('Precaución'); break
    case "verde": console.log('Adelante'); break
    default: console.log('Error'); break
}
```

![JS Condicionales](img/js-conditions.JPG)

* **Bucles**: un bucle, o ciclo de repetición, es una estructura de control que me permite ejecutar cierto código mientras se cumpla una condición. A diferencia del condicional, una vez ejecutado el código, si la condición se sigue cumpliendo el código se vuelve a ejecutar.

```javascript
var x = 1
while (x < 10) {
    console.log(x)
    x++
}

var arr = ["ub", "uade", "uno"]

for (var i=0; i < arr.length; i++)
    console.log(arr[i])

for (var dato of arr)
    console.log(dato)

```

## Funciones

* Una función es un sub-programa o porción del código que cumple una tarea específica.
* Podemos llamarlas todas las veces que necesitemos realizar dicha tarea.
* Pueden recibir datos externos (parámetros) separados por comas.
* Pueden devolver un valor
* Dentro de una función podemos crear variables según sea necesario. Debemos tomar en cuenta que las variables creadas dentro de una función existirán ÚNICAMENTE dentro de la función que las creó.

```javascript
// Function declaration
function square(x) {
    return x*x
}

// Function Expression
const square = function(x) { return x*x }

// Arrow Function 
const square = (x) =>  { return x*x }


square(3)
```

## Arguments

* En toda función de Javascript existe el objeto "arguments" , un arreglo donde se almacenan todos los datos de entrada de la función.

```javascript
function suma(v, w, x, y, z) {
    var resultado = 0;
    for(var i = 0; i < arguments.length; i++)
        resultado += arguments[i]
    return resultado
}
console.log(suma(2, 4, 6, 8, 10))  // muestra 30
```

* En el ejemplo anterior, se obtiene el resultado sin tocar los parámetros.
* Podríamos no darle ningún parámetro y utilizar el objeto arguments.

```javascript
function suma() {
    var resultado = 0;
    for(var i = 0; i < arguments.length; i++)
        resultado += arguments[i]
    return resultado
}
console.log(suma(2, 4, 6))         // muestra 12
console.log(suma(2, 4))            // muestra 8
console.log(suma(2, 4, 6, 8, 10))  // muestra 30
```

## Funciones predefinidas

```javascript

Number("1.95")  // 1.95
Number(true)    // 1
Number("hola")  // NaN

String(1.95)     // "1.95"
String(true)     // "true"
String("Hola")   // "Hola"

parseInt("1.95")   // 1
parseFloat("1.95") // 1.95
```

## Programación orientada a objetos (POO)

* Un objeto es un tipo de dato o estructura que me permite describir cosas reales.
* Poseen datos (propiedades o atributos) y las funciones (métodos) que manejan éstos.
* Ejemplo: Objeto coche
  * Propiedades = {color, modelo, marca}
  * Método = {arrancar, acelerar, frenar}

* Instancias: todas parten de la misma estructura base, pero sus propiedades toman distintos valores.
* Ejemplo: Instancia miCoche
  * Propiedades = {color: rojo, modelo: EcoSport, marca: Ford}
  * Método = {arrancar, acelerar, frenar}

```javascript

// Constructor "de un solo uso"
var unCoche = {marca: "Ford", modelo: "EcoSport", color: "rojo" }
unCoche.marca

function MiCoche(vMarca, vModelo, vColor) {
    this.marca = vMarca
    this.modelo = vModelo
    this.color = vColor
    this.arrancar = function(velocidad) { ... }
}

var unCoche1 = new MiCoche("Ford", "EcoSport", "rojo")
var unCoche2 = new MiCoche("Chevrolet", "Trucker", "gris")
unCoche1.marca
unCoche1.arrancar(60)
```

* Ejemplo: Punto

```javascript
function Punto(x, y) {
    this.x = x
    this.y = y
    this.getX = () => this.x
    this.getY = () => this.y
    this.distOrigen = () => Math.sqrt(Math.pow(2, this.getX()) + Math.pow(2, this.getY()))
}

var p = new Punto(3, 4)
p.distOrigen()
```

## Objetos de JS

* Objeto Boolean

```javascript
var b = new Boolean()  // false
```

* Objeto Number

```javascript
var n = new Number(5)
```

* Objeto String
  * Estos métodos no modifican la instancia, por lo que se debe almacenar su valor en una variable si se quiere usar el resultado posteriormente.

```javascript
var s = new String("Hola")
s.length        // 4
s.charAt(0)     // H
s.indexOf("a")  // 3
s.concat(" PP") // "Hola PP"
s.toLowerCase() // "hola"
s.toUpperCase() // "HOLA"
s.substring(1,3)// "ol"
s.substring(1)  // "ola"
s.split ("l")   // ["Ho", "a"]
s.replace("H","B") // "Bola"
" Hola   ".trim()  // "Hola" 
```

![Strings](img/js-strings.JPG)

* Objeto Array

```javascript
var arr = new Array()
var arr = ["lun", "mar", "jue"]
arr.length           // 3
arr.join("-")        // "lun-mar-jue"
arr.pop()            // ["lun", "mar"] devuelve "jue"
arr.push("vie")      // ["lun", "mar", "jue", "vie"]
arr.shift()          // ["mar", "jue"] devuelve "lun"
arr.unshift("dom")   // ["dom", "lun", "mar", "jue"]
arr.reverse()        // ["jue", "mar", "lun"]
arr.sort()           // ["jue", "lun", "mar"]

arr[0]               // "lun"
arr[0] = "dom"  

var nums = [1, 2, 3, 4, 5]
nums.every(num => num > 3) // false, verifica si c/u cumple con la condición
nums.some(num => num > 3)  // true, verifica si alguno cumple con la condición
nums.map(num => num * 2)   // [2, 4, 6, 8, 10], transforma los elementos
```

![Arrays](img/js-array.JPG)

* Objeto Date
  * Almacena la fecha como un número que representa los milisegundos que han pasado desde el 1/1/1970 a las 00:00:00.000.

```javascript
var f0 = new Date()              // fecha y hora actual
var f1 = new Date(96400000)      // 2/1/1970 00:00:00
var f2 = new Date(2008, 7, 15)   // 15/08/2008
var f3 = new Date(2008, 7, 15, 13, 25, 34) // 15/08/2008 13:25:34
var f4 = new Date(“2008-08-15”)  // 15/08/2008


f0.getTime()
f0.getMinutes()
f0.getDate()
f0.getDay()
f0.getFullYear()

fo.toDateString()
f0.toLocaleDateString()
f0.toTimeString()
f0.loLocaleString()
f0.toString()
```

* Objeto Math

```javascript
Math.E
Math.PI
Math.pow(2, 3)  // 9
Math.sqrt(9)    // 3
Math.random()   // 0.04825
```

* Objeto RegExp

```javascript
var p1 = new RegExp("hola+")   // hola, holaa, holaaa, ...
var p2 = new RegExp("^A")      // lineas que empiezan con A
var p3 = new RegExp("\\d\\d")  // número de 2 dígitos
var p4 = new RegExp("\\d{2}-\\d{2}-\\d{4}") // formato fecha dd-dd-dddd


var texto = "Este mes aprendo JavaScript"
new RegExp("/va/").test(texto)  // true
new RegExp("/lol/").test(texto) // false
new RegExp("/apr/").exec(texto) // ["apr"]
```

## Debug

1. Presionar F12
1. Solapa "Consola"
1. Escribir código o ver resultados de código mediante sentencia console.log()

## Ejemplo Maze

```javascript
class Maze {
    constructor(x, y) {
        this.x = x
        this.y = y
        this.board = [this.x]
        for(var i = 0; i < this.x; i++) {
            this.board[i] = []
            for(var j = 0; j < this.y; j++)
                this.board[i][j] = "."
        }
        this.xActual = Math.floor(this.x / 2)
        this.yActual = Math.floor(this.y / 2)
        this.setValueInActualPosition("v")
    }
    printMaze() {
        var myBoard = ""
        for(var i = 0; i < this.x; i++) {
            for(var j = 0; j < this.y; j++)
                myBoard += this.board[i][j] + " "
            myBoard += "\n"
        }
        console.log(myBoard)
    }
    setValueInActualPosition(aDirection) {
        this.board[this.xActual][this.yActual] = aDirection
    }
    getValueOfActualPosition() {
        return this.board[this.xActual][this.yActual]
    }
    packmanRight() {
        this.setValueInActualPosition("<")
    }
    packmanLeft() {
        this.setValueInActualPosition(">")
    }
    packmanRight() {
        this.setValueInActualPosition("<")
    }
    packmanUp() {
        this.setValueInActualPosition("v")
    }
    packmanDown() {
        this.setValueInActualPosition("^")
    }
    tick() {
        var actualValue = this.getValueOfActualPosition()
        this.setValueInActualPosition(" ")
        switch(actualValue) {
            case "<":
                (this.yActual == this.y - 1)? this.yActual = 0 : this.yActual += 1
                this.packmanRight()
                break
            case ">":
                (this.yActual === 0)? this.yActual = this.y - 1 : this.yActual -= 1
                this.packmanLeft()
                break
            case "v":
                (this.xActual === 0)? this.xActual = this.x - 1 : this.xActual -= 1
                this.packmanUp()
                break
            case "^":
                (this.xActual == this.x - 1)? this.xActual = 0 : this.xActual += 1
                this.packmanDown()
                break
        }
    }
}

var maze = new Maze(5, 5)
maze.printMaze()
maze.packmanRight()
maze.tick()
maze.printMaze()

```

## DOM

* Document Object Model
* Es un modelo creado por el navegador al momento de cargar una página.
* Este modelo describe a la página como objetos de Javascript.
* El DOM se representa como un árbol de objetos (parecido a un árbol genealógico) en el cual todos los elementos contenidos por otro elemento se considerarán "hijos".
* Ejemplo:

![Página HTML](img/dom-html.png)

![DOM](img/dom-arbol.png)

* ¿Qué nos permite hacer esto con Javascript?
  * Modificar elementos
  * Modificar atributos
  * Modificar estilos de CSS
  * Eliminar elementos y atributos
  * Agregar elementos y atributos

## Objetos del DOM

* **Window**: encargado de representar la ventana del navegador donde se está visualizando la página.

```javascript
var v1 = window.open("mi_pagina.html")
var v2 = window.open("mi_pagina.html", "titulo", "width=200, height=300, top=100, left=400")
```

* **Navigator**: se puede acceder a información acerca del navegador que está utilizando el usuario para ver la página.

```javascript
navigator.appName
navigator.appVersion
navigator.userAgent
navigator.language
navigator.cookieEnabled
```

* **Screen**: se obtiene información de la configuración de pantalla del usuario que está viendo la página.

```javascript
screen.width
screen.height
screen.colorDepth
```

* **History**: se encarga de almacenar el historial de visitas del navegador.

```javascript
history.length
history.back()
history.forward()
history.go(posicion)
```

* **Location**: contiene la URL actual, de la cual se podrá obtener una serie de valores.

```javascript
location.href
location.hostname
location.pathname
location.search
location.port
location.protocol
location.assign("http://www.google.com")  // se redirecciona a otra página
location.reload()                         // recarga la página actual idem F5
```

* **Document**: cuando se visualiza una página Web, todos sus elementos (texto, imágenes, enlaces, formularios...) quedan representados y accesibles para el código dentro del objeto document.

```javascript
var miAncla = document.anchors[0]
var miForm = document.forms["formNuevoUsuario"]
var miImage = document.images["logo"]
var miLink = document.links[3]
var miScript = document.scripts[0]

document.doctype
document.title
document.lastModified

document.write("Esto es un texto <B> en negrita </B>")
document.getElementById("unId")
document.getElementsByName("unName")
document.getElementsByTagName("div")
document.getElementsByClassName("botones")
document.querySelector("#unId")

<p id="p1">Texto del párrafo</p>
var p = document.getElementById("p1")
p.innerHTML = "<i>Texto nuevo</i>"
```

![Funciones para ubicar elementos](img/document-getElement.png)

* Pasos para agregar un elemento a la página:
  1. var titulo = document.createElement(“h2”);
  1. titulo.innerText = “Título creado en JS”;
  1. document.body.appendChild(titulo);

* Agregar atributos:
  1. titulo.setAttribute("style", "color:#35FF54")

* **Anchor**: engloba todas las propiedades y métodos que tienen los enlaces internos al documento, también llamados anclas y anchor.

```javascript
<a id="lstProp" name="listado" target="_self">Ver Listado de <b>propiedades</b></a>
var a = document.anchors["listado"]
a.id           // lstProp
a.name         // listado
a.target       // _self
a.text         // Ver Listado de propiedades
a.innerHTML    // Ver Listado de <b>propiedades</b>
a.focus()
a.blur()
```

* **Link**: permite acceder a todos los enlaces externos al documento o página actual. Se consideran objetos link todos los elementos HTML con etiquetas \<area> y los \<a> con el atributo href definido (aunque tengan también valor en name).

```javascript
<a id="lstProp" href="pag3.php#propiedades" target="_blank">Ver Listado de <b>propiedades</b></a>
var l = document.links[0]
l.id          // lstProp
l.href        // ...pag3.php#propiedades
l.target      // _blank
l.hostname
l.pathname
l.port
l.protocol
l.text
l.innerHTML
l.focus()
l.blur()
```

* **Image**: permite acceder y manipular ciertas características de una imagen contenida en la página.

```javascript
<img id="imgLogo" name="logo" src="img/logo.jpg" width="120" height="45" alt="Logo de la empresa" title="Este es nuestro logo"></img>
var i = document.images[0]
i.id
i.name
i.src
i.width
i.height
i.alt
i.title
```

## Forms

* **Form**: el objeto document permite un acceso directo a todos los formularios de la página a través de la colección forms.

```javascript
// accesos
var f = document.forms[0]
var f = document["formRegistro"]
var f = document.formRegistro

// acceso a un campo
var c = f.elements[0]
var c = f.elements["nombreUsuario"]
var c = f.nombreUsuario

f.name
f.length
f.action
f.method

f.reset()  // limpia el formulario
f.submit() // envia el formulario

c.name
c.id
c.type
c.value
c.disabled
c.readOnly
c.maxLength
c.size

// Campos de entrada de datos: text, textarea, password, file, hidden
c.focus()
c.blur()
c.select()  // selecciona el texto que esta escrito dentro de la caja de texto

// Campos de selección de datos: select, radio, checkbox
sel.options[0]
sel.multiple
sel.selectedIndex

rad.value
rad.checked
rad.click()

che.value
che.checked
che.click()

// Botones: button, submit, reset
b.click()
```

## Ejemplo validación form

```html
<h3>Formulario para darse de alta como usuario en nuestra Web</h3>
<form id="form" name="formRegistro" action="registrar.php" method="post">
    Username: <input type="text" id="ent1" name="usuario" maxlength="8" />(Máximo 8 caracteres) <br>
    Password: <input type="password" id="ent2" name="clave" /> <br>
    Repetir:  <input type="password" id="ent3" name="claveRepe" />(Deben coincidir) <br>
    Email:  <input type="text" id="ent4" name="email" size="40" />
    Idioma: <select id="sel1" name="idioma">
                <option id="opc1" value="EN">Inglés</option>
                <option id="opc2" value="ES" selected>Español</option>
                <option id="opc3" value="PT">Portugués</option>
            </select> <br> <br>
    <input type="checkbox" id="sel2" name="publicidad" />Quiero recibir publicidad mensual en mi mail <br>
    <a href="javascript:validarRegistro()">Validar formulario</a>
</form>
<script>
    function comprobarUsuario(nombreUsuario) {
        return nombreUsuario != ""
    }
    
    function comprobarContraseña(clave, claveRepetida) {
        if (clave != "" && claveRepetida != "")
            return clave == claveRepetida
        return false        
    }

    funtion comprobarEmail(email) {
        var patron = new RegExp("^\\w+@\\w+\\.\\w{2,3}$")
        if (email != "")
            return patron.test(email)
        return false
    }

    function comprobarIdioma(campoIdioma) {
        return campoIdioma.selectedIndex != -1
    }

    function comprobarPublicidad(aceptaPublicidad) {
        if (!aceptaPublicidad)
            return confirm("Nuestra publicidad le mantendrá informado sobre las ofertas y novedades. ¿Desea recibirla en su mail?")
        return true
    }

    function validarRegistro() {
        with (document.formRegistro) {
            if (!comprobarUsuario(usuario.value)) {
                alert("El nombre de usuario está vacío.")
                usuario.focus()
            } else if (!comprobarContraseña(clave.value, claveRepe.value)) {
                alert("La contraseña está vacía o no coinciden.")
                clave.value = ""
                claveRepe.value = ""
                clave.focus()
            } else if (!comprobarEmail(email.value)) {
                alert("El email está vacío o no es válido.")
                email.select()
                email.focus()
            } else if (!comprobarIdioma(idioma)) {
                alert("No hay idioma seleccionado.")
                idioma.focus()
            } else 
                publicidad.checked = comprobarPublicidad(publicidad.checked)
        }
    }
</script>    
```

## Eventos

* Acciones que puede hacer el usuario en la página Web.
* Engloban cosas como pasar el puntero del mouse por encima de una imagen o hacer clic sobre un botón.
* JavaScript es capaz de detectar estos eventos y, a la vez, permite asociarles unas instrucciones que se ejecutarán cuando se produzcan.

| Evento | Origen | Elementos html que generan eventos |
| -- | -- | -- |
| abort | la carga de una imagen es interrumpida | img |
| **load** |la página se termina de cargar | body |
| unload | se abandona la página actual | body |
| error | se produce un error durante la carga de un documento o imagen | body, img |
| resize | se modifica el tamaño de una ventana o marco | body |
| blur | un elemento de la página pierde el foco | body, input, select, textarea |
| focus | un elemento recibe el foc | body, input, select, textarea |
| **change** | se modificó un elemento de HTML | input, select, textarea |
| select | se selecciona un elemento de la página | input, textarea |
| **keydown** | el usuario aprieta una tecla | elem. de entrada de datos |
| keyup | una tecla que estaba pulsada es soltada | elem. de entrada de datos |
| keypress | una tecla es pulsada. Se genera después de KeyDown | elem. de entrada de datos |
| **click** | el usuario hizo click sobre un elemento | elem. de selección de datos, botones, a, img |
| dblclick | se hace doble clic sobre un  elemento | elem. de selección de datos, botones, a, img |
| mousedown | se pulsa un botón cualquiera del mouse | elem. de selección de datos, botones, a, img |
| mouseup | se libera un botón del mouse que estaba pulsado | elem. de selección de datos, botones, a, img |
| mousemove | se mueve e l puntero por la pantalla | elem. de formulario, a, img |
| **mouseover** | el usuario mueve el mouse sobre un elemento | elem. de formulario, a, img |
| **mouseout** | el usuario mueve el mouse fuera de un elemento | elem. de formulario, a, img |
| submit | un formulario está a punto de ser enviado | form |
| reset | un formulario es limpiado o reiniciado | form |

* Un evento como tal carece de utilidad por sí mismo.
* Se hace necesario asociarles una función o código JavaScript que se ejecutará cuando se produzca dicho evento.
* A estas funciones o código se les conoce como manejadores de eventos.
* Nombre de los manejadores se definen anteponiendo la palabra "on" al nombre del evento. Ejemplo onclick.

```html
<body>
    <input type="button" id="btn" name="mensaje" value="Púlsame" onclick="alert('Me has pulsado!')" />
</body>
```

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Calculadora</title>
        <meta charset="UTF-8">
        <script type="text/javascript" src="programa.js"></script>
    </head>
    <body onload="alert('página cargada')">
        <button onclick="alert('botón clickeado')">Clickeame!</button>
        <h1 onmouseover="this.innerText='que tal?'" onmouseout="this.innerText='Hola!'">Hola!</h1>
        <input type="text" onchange="alert('texto modificado')">
    </body>
</html>
```

```html
<form name="formEventos">
    <h3>Listado de Eventos</h3>
    <textarea name="eventos" rows="9"></textarea>
</form>
<script>
    function mostrarEvento(evento) {
        document.formEventos.eventos.value += eventos.type + "\n"
    }
    document.onclick = mostrarEvento
    document.onmousedown = mostrarEvento
    document.onmouseup = mostrarEvento
</script>
```

## Event Listeners

* Podemos establecer desde Javascript que un elemento de HTML esté a la espera de que un evento ocurra utilizando el método **addEventListener**.
* El método **addEventListener** recibe dos parámetros, el evento a escuchar (sin el prefijo "on") y la función a ejecutar (el handler) cuando el evento ocurra.

```javacript
elemento.addEventListener(event , handler)
```

## AJAX

* JavaScript Asíncrono y XML (AJAX).
* Es un conjunto de técnicas de desarrollo web que permiten evitar las demoras que pueden presentarse en las clásicas peticiones y posteriores resultados del servidor; para lograrlo se encarga de transmitir pequeños paquetes de datos en segundo plano.
* Entonces, la principal característica de AJAX reside en que hace posible efectuar peticiones al servidor y obtener resultados en segundo plano. Luego, utiliza los datos obtenidos para modificar los contenidos presentes en la página con la posibilidad de ofrecer efectos dinámicos y que se desplieguen con rapidez.
* Esto es posible pues no se necesita recargar la página por completo como sucede con otras tecnologías que realizan peticiones al servidor.
* Crea aplicaciones más rápidas y con mejor respuesta a las acciones del usuario.
* Aplicaciones web como Gmail, Facebook, Twitter, hacen uso de AJAX para mejorar la experiencia de usuario, ya que muchas de las consultas que se realizan al servidor no requieren recargar toda la página y muestran la información recibida del servidor de una manera rápida y precisa.

### Pasos

1. Usuario realiza una acción en la página.
1. Se invoca a XMLHttpRequest para iniciar la petición al servidor.
1. Se ejecuta una petición asíncrona.
1. Servidor procesa los datos recibidos y devuelve un XML con la información necesaria.
1. XMLHttpRequest interpreta el XML y reparte la información a los lugares que corresponde.
1. Se actualiza solo aquella parte de la página requerida por los datos, es escrita y se forma el objeto DOM con los nuevos datos.

### Ejemplo

```html
<body>
    <button type="button" onclick="cargar_paises()">Obtener Países</button> <br> <br>
    <table id="paises"></table>
    <script>
        function cargar_paises() {
            // Permite realizar la comunicación con el servidor en segundo plano
            var xmlhttp = new XMLHttpRequest()
            xmlhttp.onreadystatechange == function() {
                // readyState: representa la situación del intercambio de datos a través del objeto
                // 0: no iniciado, 1: conexión con servidor establecida, 2: recibida petición en servidor, 3: enviando información, 4: completado
                // status: código enviado por el servidor que indica el tipo de respuesta dada a la petición
                // 200: OK, 404: no encontrado, 500: error interno del servidor
                if (this.readyState == 4 && this.status == 200)
                    procesarRespuesta(this)
            }
            // Crea la petición para el servidor
            xmlhttp.open("GET", "http://api.mercadolibre.com/classified_locations/countries")
            // Envia la petición al servidor
            xmlhttp.send()
        }

        function procesarRespuesta(xmlhttp) {
            // responseText: contiene la respuesta del servidor en formato texto
            var json = JSON.parse(xmlhttp.responseText)
            var table =  "<tr> <th> Name </th> <th> currency_id </th> </tr>"
            for(var i=0; i < json.length; i++)
                table += "<tr> <td>" + json[i].name + "</td> <td>" + json[i].currency_id + "</td> </tr>"
            document.getElementById("paises").innerHTML = table
        }
    </script>
</body>
```

## JQuery

* Creada en 2006 por John Resig.
* Es una librería JavaScript, gratuita con licencia GNU.
* Simplifica las tareas de:
  * Manipulación HTML/DOM.
  * Manipulación CSS.
  * Métodos para los eventos HTML.
  * Efectos y animaciones.
  * AJAX
  * Utilidades
* En la sección descargas de jquery.com [JQUERY](http://jquery.com/download/) se pueden encontrar las diversas formas de incluir la librería en un proyecto.

```html
<html>
<head>
    <meta charset="utf-8">
    <title>jQuery</title>
</head>
<body>
    <h1>HTML</h1>
    <script src="jquery-3.3.1.min.js"></script>
    <script>
        $('h1').html('jQuery está en la casa')
    </script>
</body>
</html>
```

* Sintaxis básica: $(selector).action()
  * $(this).hide()     // oculta el elemento actual
  * $("p").hide()      // oculta todos los elementos \<p>
  * $(".test").hide()  // oculta todos los elementos con class = "test"
  * $("#test").hide()  // oculta el elemento con id = "test"

* Funciones:

| Función | Descripción |
| -- | -- |
| html() | devuelve contenido html |
| html('Un poco de \<em> markup </em>') | asigna nuevo html |
| text() | devuelve contenido textual |
| text('Pepe') | asigna contenido textual |
| empty() | equivale a html('') |
| css('color') | devuelve valor de la prop css |
| css('color', 'red') | asigna el estilo css |
| attr('src') | devuelve el valor del atributo |
| attr('src', 'http://' | asigna un nuevo valor al atributo |

* Eventos:
  * click(callback)
  * change(callback)
  * blur(callback)
  * focus(callback)
  * submit(callback)
  * hover(callback)
  * hover(callbackIn, callbackOut)
  * [Otros eventos](http://api.jquery.com/category/events/))

```javascript
$(‘#btn1’).click(function(){ 
     console.log(“click”);
});

```

* Método $.ajax

```javascript
$.ajax({
     url:'mi-archivo.html'
})
.done(recibir)
.fail(manejarError);

function recibir(datos){
     $('#miDiv' ).text(JSON.stringify(datos));
}

function manejarError() {
    alert(‘Se produjo un error’);
}
```

### Ejemplo: Mover cuadrado con animate

```html
<button>Mover el cuadrado</button>
<div id="cuadrado"></div>
```

```css
div {
  background: blue;
  height: 100px;
  margin: 10px;
  position: absolute;
  width: 100px;
}
```

```javascript
$(document).ready(function(){
    $("button").click(function(){
        $("#cuadrado").animate({
            height: '150px', 
            left: '500px',
            opacity: '0.7',
            top: '100px',
            width: '150px'
        }, 1500);
    });
});
```

### Ejemplo: bola con time

```html
<div id="bola"></div>
```

```css
#bola {
  width: 10px;
  height: 10px;
  background-color: red;
  border: black 2px solid;
  border-radius : 10px;
  position: relative;
}
```

```javascript
$(function(){
  function animarBola() {
    $("#bola").animate({left: '+=150'}, "slow")
              .animate({top: '+=150'}, "slow")
              .animate({left: '-=150'}, "slow")
              .animate({top: '-=150'}, "slow");   
  }
  
  setInterval(animarBola, 2400);
});
```

### Ejemplo: Reloj

```html
<span id="hora"></span>
```

```css
* {
    font-family: Helvetica;
    font-size: 20px;
    text-align: center;
}
```

```javascript
$(function() {
    function mostrarHora() {
        var fecha = new Date(), // nuevo objeto Fecha
        hora = fecha.getHours() + ":" + fecha.getMinutes() + ":" + fecha.getSeconds();
         $('#hora').text(hora);
    }
    setInterval(mostrarHora, 1000); // la función "mostrarHora" se ejecuta cada segundo
});
```

## Ejercicios

1. Hacer un programa que tome dos valores por teclado y los multiplique, luego muestre el resultado por pantalla, por ambos métodos (alert y console.log)
1. Realizar un programa en el que se ingrese la base y la altura de un triángulo e informe su área. El programa debe imprimir una leyenda que incluya los datos de entrada y el resultado
1. Hacer un programa en el que se ingrese la velocidad máxima de una calle, la velocidad de un auto y tipo de auto (particular o ambulancia). Las normas de tránsito indican que existe un 15% de tolerancia sobre la velocidad máxima. Indicar si el auto recibe una advertencia, una multa o nada según los siguientes parámetros:
    * Particulares:
      * Si la velocidad es menor a la velocidad máxima, no pasa nada.
      * Si la velocidad está por encima de la velocidad máxima pero dentro del margen de tolerancia = Advertencia.
      * Si la velocidad está por encima del margen de tolerancia = Multa.
    * Ambulancia:
      * Si está en una emergencia, no pasa nada.
      * Si no está en emergencia, vale como un particular.
1. Pedir al usuario que ingrese dos números por teclado y sumarlos.
1. Pedir al usuario que ingrese un número con decimales y mostrar su parte entera.
1. Pedir al usuario que ingrese un número de 4 dígitos e invertirlo.
1. Pedir al usuario que ingrese una cantidad expresada en segundos y mostrarla en días, horas, minutos y segundos.
1. Pedir al usuario que ingrese una cantidad de días, una cantidad de horas, una cantidad de minutos y una cantidad de segundos y luego expresarla en segundos.
1. Pedir al usuario que ingrese una cantidad monetaria y mostrar la cantidad mínima de billetes y monedas requerida para dicha cantidad.
1. Pedir a usuario que ingrese un número e indicar si el mismo es:
    * Par Positivo
    * Impar Positivo
    * Par Negativo
    * Impar Negativo
1. Hacer un programa que muestre una cuenta regresiva desde un valor ingresado por el usuario.
1. Hacer un programa que le pida dos números al usuario y los multiplique por el método de la suma. Ejemplo:  4x3 = 4 + 4 + 4  
1. Hacer un programa que le pida un número N  al usuario y muestre los primeros N números pares. Ejemplo: si el usuario ingresa 4, el programa mostrará: 2,4,6,8. Complicación: mostrar los números en un único mensaje.
1. Hacer un programa que le pida al usuario un número con una cantidad indefinida de dígitos e invertirlo.
1. Hacer un programa que sólo permita ingresar números pares y los muestre. Si el número ingresado es impar, mostrar un mensaje de error y pedir otro número.
1. Hacer un programa que le pida al usuario un número entero y lo muestre. El programa no deberá permitir que el usuario ingrese números con decimales ni letras. Considerar para ello que cuando las funciones parseInt y parseFloat devuelven NaN, la condición es falsa y cuando devuelven un número, la condición es verdadera. Esto no es válido para el 0, por lo que no deberán considerarlo en el programa.
1. Escribir una función que reciba el nombre de un usuario y lo salude ("Bienvenido Juan!")
1. Escribir una función que determine si una letra es vocal o no.
1. Modificar la función de las vocales para que devuelva true o false.
1. Crear una función que reciba un número binario y devuelva su equivalente en base 10.
1. Crear una función que reciba un número entero y devuelva:
     * Verdadero si el número ingresado es primo.
     * Falso si el número ingresado no es primo.
1. Crear una función que reciba los datos de un usuario y devuelva un objeto "usuario" con dichos datos almacenados en el.
1. Hacer una función que le cargue a un objeto alumno (ya existente) las notas de las materias
1. Crear un arreglo de números y mostrar su longitud, luego agregarle datos y volver a mostrar su longitud. Finalmente, eliminar los últimos 3 valores del arreglo y mostrarlo.
1. Cargar un arreglo de “marcas” con datos ingresados por el usuario.
1. Cargar un arreglo con los números del 1 al 1000.
1. Pedirle al usuario una cantidad y eliminar esa cantidad de números del arreglo anterior.
1. Considerando un eje de coordenadas cartesiano de dos dimensiones (x,y) pedirle al usuario dos puntos del plano e indicar cual se encuentra más cercano al (0,0) y luego indicar la distancia entre dichos puntos. Cada punto del plano es un arreglo de dos elementos.
1. Utilizando el arreglo de números del 1 al 1000, pedirle al usuario un número entero y buscarlo dentro del arreglo. Si se encuentra el número, indicar en qué posición está; en caso contrario mostrar un mensaje indicando que el número no está en el arreglo.
1. Utilizando un ciclo for, recorrer un arreglo de los ejercicios anteriores (elegir uno) de principio a fin mostrando de manera independiente todos los valores que se encuentran en el.
1. Pedir números positivos al usuario, cargar un arreglo con todos los números pares que haya ingresado. Luego, recorrer el arreglo e indicar cuál fue el mayor número guardado. La carga de números finaliza cuando el usuario ingrese el 0.
1. Pedir números al usuario y almacenar en un arreglo los primeros 10 números pares ingresados, mostrarlo. Luego, eliminar los primeros 3 números del arreglo.
    * Dato: no podemos eliminar un valor del principio, pero si podemos reemplazarlo por otro y luego eliminar el último valor del arreglo.
    * Condición: el arreglo debe mantener el orden original.
1. Utilizando el arreglo anterior, pedirle un número al usuario
    * Si el número está en el arreglo, eliminarlo.
    * Si el número NO está en el arreglo, indicarlo.

## Ejercicios DOM

1. Crear una página con HTML con algunos elementos a elección (al menos un título).
    * Ubicar un elemento (a elección) y cambiar su contenido.
    * Luego ubicar otro elemento y ponerlo en negrita.
1. En la página creada anteriormente, utilizar javascript para crear una lista no ordenada con tres elementos y darles color.
1. Escribir el código JS para que al apretar el botón, se sumen X1 y X2 mostrándose el resultado en el título con id="resultado".
    * generar evento click en el botón.
    * cuando se aprieta, tomar lo que hay en la propiedad value de los inputs y almacenarlo en alguna variable.
    * sumar las variables y mostrar el resultado en el contenido del h2

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <title>Estilos</title>
            <meta charset="UTF-8">
        </head>
        <body>
            <h1>¡SUMAS SUMAS SUMAS!</h1>
            <p>Ingresá un número en cada casilla para sumarlos.</p>
            <input id="x1" type="text" placeholder="x1"><br>
            <input id="x2" type="text" placeholder="x2"><br>
            <button>Sumar!</button>
            <h2 id="resultado"></h2>
        </body>
    </html>
    ```

1. Hacer una calculadora con 15 botones: 10 Dígitos, 4 Operaciones, 1 Igual. Escribir el código HTML correspondiente. recordar que deben dejar un espacio para el resultado. Luego mediante JS programar todos los eventos y los handlers.
1. Implementar la siguiente página web:
    ![Ejercicio Personas](img/ejercicio-personas.JPG)
1. Escribe un programa que contenga un formulario con cinco botones. Cada uno de los botones debe tener como etiqueta el nombre de un color y al pulsarlo pondrá el color del fondo del documento del mismo color que indica.
1. Como ampliación del ejercicio anterior, añade a los cinco botones, la posibilidad de elegir el cambio de color para el fondo del documento o para el fondo de una capa situa da en la esquina superior derecha del documento. (sugerencia.- Usar un formulario del tipo type=' radio' para elegir entre cambiar el documento o la capa).
