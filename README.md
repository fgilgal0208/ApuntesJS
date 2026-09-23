# Apuntes JavaScript - Fundamentos (Exercism)

## 1. Variables (Declaración y Asignación)
Para almacenar datos en memoria se utilizan `let` y `const`.
* **`const`**: Para valores que **no** van a cambiar (constantes).
* **`let`**: Para variables cuyo valor se reasignará en el futuro.

```javascript
const birthYear = 1990; // No cambiará
let age = 33;
age = 34; // Se puede reasignar
```

## 2. Booleanos (Booleans) y Operadores Lógicos
Solo admiten `true` (verdadero) o `false` (falso). Se combinan con operadores lógicos:
* **AND (`&&`)**: Verdadero si ambos son verdaderos.
* **OR (`||`)**: Verdadero si al menos uno es verdadero.
* **NOT (`!`)**: Invierte el valor.

```javascript
const isAdult = true;
const hasLicense = false;

const canDrive = isAdult && hasLicense; // => false
const canDrink = isAdult || hasLicense; // => true
const isNotAdult = !isAdult; // => false
```

## 3. Números y Operadores Aritméticos
JavaScript usa el tipo `Number` tanto para enteros como para decimales.
* **Operadores:** Suma (`+`), resta (`-`), multiplicación (`*`), división (`/`), módulo o resto (`%`), exponenciación (`**`).
* **Prioridad (PEDMAS):** Paréntesis, Exponentes, División/Multiplicación, Suma/Resta.
* **Asignación abreviada:** Atajo para operar y reasignar (`+=`, `-=`, etc.).

```javascript
2 - 1.5; // => 0.5
40 % 4; // => 0
4 ** 3; // => 64

// Orden de precedencia
const result = 3 ** 3 + 9 * 4 / (3 - 1); // => 45

// Asignación abreviada
let x = 5;
x += 25; // x es ahora 30
```

## 4. Incremento y Decremento
Modifican una variable numérica sumando o restando 1 directamente.
* **`++`**: Suma 1.
* **`--`**: Resta 1.

```javascript
let i = 3;
i++; // i es ahora 4

let j = 0;
j--; // j es ahora -1
```

## 5. Strings (Cadenas de texto)
Almacenan texto usando comillas simples (`' '`), dobles (`" "`) o acentos graves (`` ` ` ``).
* **Acceso y Longitud:** Son como listas (índice inicial `0`). Se usa corchetes para acceder y `.length` para la longitud.
* **Concatenación:** Se unen con el operador `+`.
* **Inmutabilidad:** Los métodos siempre devuelven un string nuevo.

```javascript
'cat'[1]; // => 'a'
'cat'.length; // => 3

// Concatenación
'I like' + ' ' + 'cats.'; // => "I like cats."

// Métodos
let word = '  hello  ';
word.trim().toUpperCase(); // => "HELLO"
```

## 6. Comparaciones
Evalúan igualdades o diferencias. 
* **Igualdad estricta (`===` y `!==`):** Compara valor y tipo (siempre recomendada).
* **Relacionales:** `<`, `>`, `<=`, `>=`.

```javascript
3 === 3; // => true
3 === '3'; // => false (distinto tipo)
5 !== 4; // => true
10 >= 5; // => true
```

## 7. Condicionales
Controlan el flujo del programa basándose en condiciones booleanas.

```javascript
let score = 85;

// if, else if, else
if (score >= 90) {
  console.log("A");
} else if (score >= 80) {
  console.log("B");
} else {
  console.log("C");
}

// Operador Ternario (Condición ? True : False)
const status = score >= 50 ? 'Pass' : 'Fail';
```

## 8. Arrays (Arreglos)
Listas sin longitud fija que pueden contener cualquier tipo de dato. Se crean con corchetes `[ ]`.
* **Métodos que mutan el array:** `push()` (añade al final), `pop()` (elimina del final), `unshift()` (añade al principio), `shift()` (elimina del principio).

```javascript
const numbers = [1, 'two', 3, 'four'];

numbers[2]; // => 3
numbers.length; // => 4
numbers[0] = 'one'; // Modifica el primer elemento

// Añadir y quitar elementos
numbers.push(5); // => ['one', 'two', 3, 'four', 5]
numbers.shift(); // Elimina y devuelve 'one'
```

## 9. Bucles (For, While, Do-While)
Ejecutan bloques de código de forma repetitiva.
* **Control:** `break` (detiene el bucle por completo) y `continue` (salta a la siguiente iteración).

```javascript
// Bucle For (ideal para arrays)
const list = ['a', 'b', 'c'];
for (let i = 0; i < list.length; i++) {
  console.log(list[i]);
}

// Bucle While
let count = 0;
while (count < 10) {
  if (count === 5) {
    count++;
    continue; // Salta cuando count es 5
  }
  count++;
}
```

## 10. Sentencia Switch
Alternativa a múltiples `if` para comparar una sola variable contra varios valores específicos usando igualdad estricta.

```javascript
let color = 'red';

switch (color) {
  case 'red':
    console.log('Stop');
    break; // Crucial para que no siga ejecutando los de abajo
  case 'yellow':
    console.log('Caution');
    break;
  case 'green':
    console.log('Go');
    break;
  default:
    console.log('Invalid color');
}
```

## 11. Null y Undefined
Representan la ausencia de valor, pero de formas distintas:
* **Null:** Valor "vacío" asignado intencionalmente por el programador.
* **Undefined:** Ausencia total de valor (variables sin inicializar, propiedades inexistentes, etc.).

```javascript
let empty = null;
let notDefinedYet; // Su valor es undefined

// Encadenamiento Opcional (?.)
const user = { profile: { name: 'Alex' } };
console.log(user.settings?.theme); // => undefined (no da error)

// Fusión Nula (??)
let amount = null;
amount = amount ?? 10; // => 10 (asigna 10 porque es null)
```

## 12. Funciones
Bloques de código reutilizables.
* Si modificas objetos/arrays pasados como parámetros, cambias el original.
* Sin un `return` explícito, devuelven `undefined`.

```javascript
// Declaración con parámetro por defecto
function checkNumber(num = 0) {
  if (num === 0) {
    return 'You passed 0';
  }
  return 'Thanks';
}

// Devolver múltiples valores (usando un objeto)
function divide(a, b) {
  return {
    quotient: Math.floor(a / b),
    remainder: a % b,
  };
}

// Expresión de Función (Función Anónima)
const multiply = function(a, b) {
  return a * b;
};
```
