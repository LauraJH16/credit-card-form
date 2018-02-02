# Function Scope

## Objetivo:
Identificar las funciones globales, locales, funciones de callback, expresions, statement, clousure, scope, contextos de ejecucion, que funciones forman parte de la pila de ejecucion (stack execution) y que funciones forman parte de la cola de eventos (event queue).

##  Funciones Globales:
~~~
$(document).ready(function() {
});
~~~

## Funciones Locales:
~~~
$inputCard.on('input', function() {
    isValidCreditCard($(this).val().trim());
});
~~~
~~~
 function activeButton() {
    $buttonNext.attr('disabled', false);
 }
~~~
~~~
 function desactiveButton() {  
    $buttonNext.attr('disabled', true);
 } 
~~~
~~~
 function longitud(input) {
    if (input.trim().length === 16) {
      return input;
    }
 }
~~~
~~~
 function soloNumeros(input) {
    var regex = /^[0-9]+$/;
    if (regex.test(input)) {
      return input;
    }
 }
~~~
~~~
 function isValidCreditCard(numberCard) {
    var creditCardNumber = soloNumeros(longitud(numberCard));
    if (creditCardNumber !== undefined) {
      var arr = [];
      var sumaTotal = 0;
      for (var index = creditCardNumber.length - 1; index >= 0; index--) {
        arr.push(creditCardNumber[index]);
      }
      for (var index = 1; index < arr.length; index = index + 2) {
        arr[index] = arr[index] * 2;
        if (arr[index] >= 10) {
          arr[index] = arr[index] - 9;
        }    
      }
     
      for (var index = 0; index < arr.length; index++) {
        sumaTotal = sumaTotal + parseInt(arr[index]);
      }
     
      if (sumaTotal % 10 === 0) {
        console.log('Es una tarjeta valida');
        activeButton();
      } else {
        console.log('No es un numero valido');
        desactiveButton();
      }
    } else {
      console.log('Verifique el numero de su tarjeta'); 
      desactiveButton();  
    }
 }
~~~

## Funciones de Callback:
~~~
var creditCardNumber = soloNumeros(longitud(numberCard));
~~~

## Funciones Expressions:
En este caso no se ha encontrado.

## Funciones Statement:
- `activeButton`
- `desactiveButton`
- `longitud`
- `SoloNumeros`
- `isValidCreditCard`

## Clousure:
- `activeButton`
- `desactiveButton`

## Pila de ejecución:
1. `global execution context`
2. `funcion de evento ready (se ejecuta cuando el DOM cargó)`
3. `isValidCreditCard`
4. `soloNumeros`
5. `longitud`
6. `desactiveButton`
7. `activeButton`

## Cola de Eventos:
~~~
$inputCard.on('input', function() {
  isValidCreditCard($(this).val().trim());
});
~~~

### Autora:

Laura Jimenez Hidalgo





