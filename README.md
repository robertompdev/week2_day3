# week2_day3

> JS | Function declarations
> 
> JS | Context & Function invocation

## Main points: function declarations

 - Function statement: 
 ````javascript
 function name() {
   statements
 }
 ````
 
  - Function expression: 
 ````javascript
 
 function(){                           // Anónima
   statements
 }
 
 const nameFn = function(){           // Expresión de función
   statements
 }
 
 const nameFn = () => statements      // Formato flecha
 ````
 
## Main points: function are first-class objects
 
  - Las funciones, como objetos de orden superior, pueden ser tratadas como:
    - Variables
    - Valores
    - Funciones anónimas
    
## Main points: context

  - El contexto está representado por `this`, refierendo según donde se encuentre a:
    - El contexto global es el objeto `window`
      ````javascript
      this === window     // true
      ````
    - El contexto de una función es el objeto `window`
      ````javascript
      function(){
        this === window     // true
      }
      ````
    - El contexto de un método es el objeto al que pertenece
      ````javascript
      const person = {
            age: 22,
            grow() {
                this.age     // 22 
            }
      ````
    - El contexto de una función anidada en un método es el objeto `window`, a excepción del formato de función flecha, que no reorienta el contexto hacia `window`, o del uso de `.bind()` para trasnferir a la función el contexto deseado:
      ````javascript
      const person = {
            age: 22,
            grow() {
              setInterval(function(){
                this.age      // undefined
              }, 100)
                
              setInterval(function(){
                this.age      // 22
              }.bind(this), 100)
                
              setInterval(() => {
                this.age      // 22
              }, 100)
           }
        }        
        ````

