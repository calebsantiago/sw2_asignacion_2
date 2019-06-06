# Asignación 2 - Ingeniería de Software 2

## Integrantes

- Guillermo Baca **20151635**
- Miguel Colina **20150346**
- Pelmef Méndez **20150865**
- Javier Ramírez **20152241**
- Caleb Santiago **20152339**

---
---

## Resúmen de Charla por Martin Fowler

La charla de Martin Fowler _Workflows of refactoring_ habla sobre los diferentes flujos de trabajo de la refactorización de una base de código. Fowler decidió hablar sobre este tema ya que observó que no se implementaban algunos de los flujos de trabajo que él considera más beneficiosos. También observó que el flujo de trabajo por el que más le preguntaban era uno que para él, en condiciones ideales, no debería de usarse.

Un concepto explicado durante la charla es que existen diferentes modos de trabajo a la hora de programar. Este concepto es explicado con una metáfora sobre sombreros en la cual el principio es que “Solo se puede programar con un sombrero puesto a la vez, pero se puede cambiar de sombrero cuantas veces se requiera”.  Los sombreros vendrían a ser los modos de trabajo a la hora de programar y los relevantes para la charla son los modos _agregar funcionalidad_ y _refactorizar_.

Los flujos de trabajo de la refactorización tocados en la charla son los siguientes:

---

### **Refactorización en desarrollo guiado por pruebas**

En este flujo de trabajo cuando se quiere añadir una nueva funcionalidad se hace de la siguiente manera: Se le añaden nuevas pruebas a la base de código y este se modifica sin tomar en cuenta la pulcritud hasta que la base de código pase todas las pruebas. Una vez terminado este paso se cambia el sombrero de _agregar funcionalidad_ por el de _refactorizar_ y se comienzan a mejorar partes del código para mejorar la pulcritud de este.

Fowler explica que se debe hacer una distinción entre  _agregar funcionalidad_ y _refactorización_ ya que tanto el objetivo cómo el ámbito en el cual se utilizan ambos modos son diferentes: A la hora de refactorizar uno espera que la base de código pase todas las pruebas y que sea fácil verificar de manera constante si los cambios alteran la funcionalidad de la base de código. A la hora de implementar funcionalidades se implementan pruebas que todavía no están aprobadas y/o de forma temporal se dejan de aprobar pruebas que antes ya se habían aprobado. 

---

### **Refactorización de recojo de basura**
Para Fowler, este flujo de trabajo es como la regla de los Boy Scouts que dice: _"Deja lo que uses mejor a como lo encontraste"_. En este flujo de trabajo la idea central es que cada vez que se encuentre código no pulcro, refactorizarlo. Fowler dice que uno no necesita dejar el código en perfectas condiciones ya que si se sigue este flujo de trabajo, por más que cada vez solo se refactorice un poco, con suficientes iteraciones las partes del código con las que más se interactúen van a quedar pulcras. En el caso de un código con el que se interactúa rara vez no es un problema que no se refactorice tan seguido ya que no es recomendable invertir mucho tiempo en refactorizar código con el cual no se interactúa mucho. 

---

### **Refactorización de comprensión**
Fowler dice que descubrir cómo funciona algo complicado y difícil de ver es bueno para una novela de detectives, pero no para una base de código. Es por esto que este flujo de trabajo plantea que cada vez que se lea código que sea difícil de entender uno debe refactorizarlo a una versión más entendible. Fowler justifica esto diciendo que si bien una vez que uno entiende el código este es fácil de modificar, la comprensión del código es momentánea y personal. Si no se refactoriza el código, cuando otra persona o uno mismo en el futuro interactúe con este se volverá a perder tiempo en descifrar que es lo que el código hace y como lo hace.

Este flujo de trabajo es bastante parecido al de la refactorización de recojo de basura, sin embargo, Fowler hace una distinción entre ambos ya que considera que son distintos en principio. Si bien todo código difícil de leer no es código pulcro, no todo código no pulcro es código difícil de leer.

![Slide 8](https://res.infoq.com/presentations/workflow-refactoring/en/slides/sl8.jpg)

---

### **Refactorización preparatoria**
Fowler define la refactorización preparatoria como la modificación del código para que este encaje de forma más fácil con las funcionalidades que se desean implementar. Este tipo de refactorización normalmente causa frustración ya que no sería necesario hacerla de haber planteado la base de código de forma diferente. Sin embargo, Fowler argumenta que esto no debería ser causa de frustración por dos razones. La primera razón es que la única forma de evitar la refactorización preparatoria es un planeamiento previo bastante detallado que pocas veces cumple con su objetivo. La segunda razón es que la refactorización preparatoria normalmente hace más rápida la implementación; no solo de las funcionalidades que se desean implementar próximamente, sino también de las que vengan en el futuro. 

![Slide 10](https://res.infoq.com/presentations/workflow-refactoring/en/slides/sl10.jpg)

---


### **Refactorización planeada**
Cuando Fowler dijo que le preguntaban bastante por un flujo de trabajo de refactorización con el que él no estaba del todo de acuerdo, se refería a este. Este flujo consiste en designar un tiempo en específico en el plan del proyecto para únicamente refactorizar el código. A Fowler no le agrada este flujo de trabajo por dos razones: Piensa que es difícil de justificar ante la gerencia y piensa que es una peor alternativa a flujos de trabajo donde la refactorización se hace de forma continua como la refactorización de recojo basura o refactorización de comprensión. Sin embargo, Fowler identifica una situación donde se justifica el uso de la refactorización planeada: Grupos de trabajo no cohesionados donde la refactorización de forma continua no es suficiente para mantener el código pulcro.

---

### **Refactorización a largo periodo**
Durante el desarrollo de software es normal que a medida que se van agregando más módulos algunas dependencias entre los módulos se vuelvan obsoletas o confusas. Sin embargo, la refactorización de los módulos y de sus dependencias puede ser un proceso complejo. Para estos casos Fowler plantea la refactorización a largo periodo la cual consiste en definir cuál es la estructura objetivo de los módulos y sus dependencias y cada vez que se trabaje en estos se modifique un poco la base del código para que esté más cerca a esa estructura objetivo. De esta forma la refactorización de módulos deja de ser un gran proceso que requiere una pausa de la implementación de funcionalidades a ser un proceso separado en pequeñas partes triviales. Esta refactorización se justifica a la hora de querer agregar nuevos componentes a la base del código ya que es más fácil de implementar un nuevo módulo a una base de código cuyos módulos y dependencias están definidos de forma clara y concisa.

---

Fowler termina la charla hablando de la hipótesis de la energía de diseño. Este concepto presenta la idea de que a medida que aumenta la complejidad del código, la pulcritud de este hace que sea más fácil o, en su defecto, más difícil implementar nuevas funcionalidades. Fowler toca este punto pues para él a la hora de justificar la refactorización del código no se debe argumentar que es por calidad, pulcritud o profesionalismo; sino más bien por un tema de optimización. Es decir, para Fowler la refactorización se debe utilizar porque está permite optimizar el ciclo de desarrollo de software: Se pueden entregar más funcionalidades en menos tiempo. Esta idea es tan intrínseca para Fowler que para evitar resistencia a la refactorización por parte de la gerencia este sugiere que no se le informe a la gerencia de esta y se asuma como parte fundamental del desarrollo de software.

![Slide 14](https://res.infoq.com/presentations/workflow-refactoring/en/slides/sl14.jpg)

---
---

## Conclusiones

Se considera que los puntos más importantes de la charla son los siguientes:

---

### **La implementación de la refactorización como parte del ciclo de desarrollo del software**

Una de las tareas más difíciles en la ingeniería de software es leer el código de otra persona. Incluso con documentación y código que ha sido refactorizado, leer código no es una tarea trivial. Hay incluso situaciones donde se evalúa volver a implementar funcionalidades en vez de refactorizarlas para evitar lidiar con código al cual no se le ha dado mantenimiento  y/o no tiene documentación. Es en este contexto que el desarrollo de código pulcro es de suma importancia para la ingeniería de software.

Los flujos de trabajo presentados ayudan al desarrollo de código más pulcro por dos razones. En primer lugar, aumentan la probabilidad de que la gerencia acepte que se haga refactorización ya que al presentarse como parte del proceso de desarrollo se deja de ver como un paso que se lleva a cabo porque alguien cometió un error o como una pérdida de tiempo. La segunda razón es que los flujos de trabajo presentados se cercioran de que la refactorización a llevar a cabo cumpla un fin: La implementación más rápida de nuevas funcionalidades. Con los flujos de trabajos presentados solo se refactoriza código con el que se  interactúa (Salvo la refactorización planeada), por lo que no se pierde tiempo en refactorizaciones que no ayuden a implementaciones de funcionalidades más rápidas.

---

### **La hipótesis de la energía de diseño**
Este concepto es importante ya que es un recordatorio a cualquier persona que es parte del desarrollo de software que, si bien en proyectos pequeños y simples prestar mucha atención a la pulcritud puede no ser necesario, esto no es el caso con proyectos de software grandes y/o complejos. Es más, esta clase de proyectos de software se ven beneficiados en gran medida por mantener un código pulcro.

---

### **El uso de la refactorización planeada**
Fowler habla de la refactorización planeada como un mal necesario ya que, si bien un equipo perfecto nunca debería tener que utilizarla, no todos los equipos pueden estar cerca a la perfección. Tener en cuenta que la refactorización planeada es una herramienta que se puede utilizar es importante, pero también es importante tener en cuenta que se si utiliza es un indicador que hay algo en el forma en que se está desarrollando el software que se puede mejorar.

---

### **Justificación de la refactorización**
Por una parte, Fowler con la hipótesis de la energía de diseño presenta un argumento conciso que cualquier persona puede utilizar para justificar la refactorización como parte del desarrollo de software. Sin embargo, por otra parte, Fowler sugiere que no se presente dicho argumento a la gerencia y que se tome como un supuesto dado que la refactorización es una parte vital del desarrollo de software. Se considera que este punto es importante ya que, independientemente si se sigue el consejo de Fowler de no argumentar sobre la refactorización con la gerencia, da las pautas necesarias para lidiar con una posible dificultad a la hora de intentar implementar la refactorización como parte importante del desarrollo de software.

---
---

## Ejemplos de Code Smells

### Ejemplo 1: Data Clumps

```typescript
class User {
  ...
  /*los siguientes métodos toman una lista de parámetros muy similares por lo que se deberán agrupar
  en una clase independiente, debido a que al tener una larga lista de parámetros podría conllevar a
  fallas del código, conflictos y difíciles pruebas de unidad*/
  searchService(name : string) : void {
    this.serviceApp.searchService(name)
  }
  requestService(name : string, date : Date, description : string) : void {
    this.serviceApp.requestService(name, date, description)
  }
  cancelService(name : string) : void {
    this.serviceApp.cancelService(name)
  }
  rateService(name : string, rate : string, comment : string) : void {
    this.serviceApp.rateService(name, rate, comment)
  }
}
```
```typescript
class Service {
  /*se utiliza la técnica de refactoring 'dividir código en piezas lógicas (extract class)' al crear 
  otra clase que agrupa a la lista de parámetros como atributos propios y utiliza métodos reservados
  de tipo 'get' para devolver dichos elementos a través de su instancia como objeto*/
  id : number
  name : string
  date : Date
  description : string
  amount : number
  status : string
  rate : string
  comment : string
  ...
  getId() : number {
    return this.id
  }
  getName() : string {
    return this.name
  }
  getDate() : Date {
    return this.date
  }
  getDescription() : string {
    return this.description
  }
  getAmount() : number {
    return this.amount
  }
  getStatus() : string {
    return this.status
  }
  getRate() : string {
    return this.rate
  }
  getComment() : string {
    return this.comment
  }
}

class User {
  ...
  /*luego de implementar la técnica de refactoring*/
  searchService(service : Service) : void {
    this.serviceApp.searchService(service)
  }
  requestService(service : Service) : void {
    this.serviceApp.requestService(service)
  }
  cancelService(service : Service) : void {
    this.serviceApp.cancelService(service)
  }
  rateService(service : Service) : void {
    this.serviceApp.rateService(service)
  }
}
```

### Ejemplo 2: Long Method

```typescript
/*se posee una clase que puede tener gran cantidad de atributos sin embargo se implementaun método el
cual busca imprimir la factura, para lo cual llama al método imprimir encabezadoy en el mismo método
imprime otros atributos lo cual en múltiples llamadas puede generar undesorden al tener un método que
llama a otro metodo ademas de hacer la llamada a otros atributos*/
class Factura {
  ...
  /*antes de la implementación de la técnica de refactoring*/
  imprimirFactura() : void {
    imprimirEncabezado()
    /*imprime los detalles correspondientes*/
    console.log(`El nombre del cliente es: ${this.nombre}`)
    console.log(`La cantidad es: ${this.cantidad}`)
    console.log(`El ruc es: ${this.ruc}`)
    console.log(`El monto es: ${this.monto}`)
    console.log(`El código es: ${this.codigo}`)
    console.log(`Es afecta de IGV: ${this.conIGV}`)
  }
}
```
```typescript
/*con la implementación del extract method nos permite tener un código mucho más comprensible y ordenado
de manera que podamos ubicar más fácilmente las llamadas y los atributos que buscamos llamar*/
class Factura {
  ...
  /*después de implementar la técnica de refactoring*/
  imprimirFactura() : void {
    imprimirEncabezado()
    imprimirDetalles()
  }
  imprimirDetalles() : void {
    console.log(`El nombre es: ${this.nombre}`)
    console.log(`La cantidad es: ${this.cantidad}`)
    console.log(`El ruc es: ${this.ruc}`)
    console.log(`El monto es: ${this.monto}`)
    console.log(`El código es: ${this.codigo}`)
    console.log(`Es afecta de IGV: ${this.conIGV}`)
  }
}
```

### Ejemplo 3: Refused Bequest

```typescript
/*se genera refused bequest cuando una subclase hereda de una superclase para reutilizar algún comportamiento
pero estas son completamente diferentes*/
class Ingeniero {
  estudiar() : string {
    return "estudiando"
  }
}
class Niño extends Ingeniero {
  ...
}
```
```typescript
/*se elimina la herencia para reemplazarla con la delegación (Replace Inheritance with Delegation)*/
class Ingeniero {
  estudiar() : string {
    return "estudiando"
  }
}
class Niño {
  private ingeniero : Ingeniero
  constructor() {
    this.ingeniero = new Ingeniero()
  }
  estudiar() : string {
    return this.ingeniero.estudiar()
  }
}
```

### Ejemplo 4: Duplicate Code

```typescript
/*si se tiene dos cases en una sentencia switch o dos ramas de if con una implementación similar, son
ejemplos de duplicate code*/
switch (i) {
  case 1:
    doFirstThing()
    doSomething()
    break
  case 2:
    doSomethingDifferent()
    break
  case 3: /*Noncompliant, duplicates case 1's implementation*/
    doFirstThing()
    doSomething()
    break
  default:
    doTheRest()
}
if (a >= 0 && a < 10) {
  doFirstThing()
  doTheThing()
}
else if (a >= 10 && a < 20) {
  doTheOtherThing()
}
else if (a >= 20 && a < 50) {
  doFirstThing()
  doTheThing() /*Noncompliant, duplicates first condition*/
}
else {
  doTheRest()
}
```
```typescript
/*la mejor solución es la combinación de las condicionales y/o cases, se puede lograr de dos formas*/
/*primera forma*/
switch (i) {
  case 1:
    doFirstThing()
    doSomething()
    break
  case 2:
    doSomethingDifferent()
    break
  case 3:
    doFirstThing()
    doThirdThing()
    break
  default:
    doTheRest()
}
if (a >= 0 && a < 10) {
  doFirstThing()
  doTheThing()
}
else if (a >= 10 && a < 20) {
  doTheOtherThing()
}
else if (a >= 20 && a < 50) {
  doFirstThing()
  doTheThirdThing()
}
else {
  doTheRest()
}
/*segunda forma*/
switch (i) {
  case 1:
  case 3:
    doFirstThing()
    doSomething()
    break
  case 2:
    doSomethingDifferent()
    break
  default:
    doTheRest()
}
if ((a >= 0 && a < 10) || (a >= 20 && a < 50)) {
  doFirstThing()
  doTheThing()
}
else if (a >= 10 && a < 20) {
  doTheOtherThing()
}
else {
  doTheRest()
}
```

### Ejemplo 5: Primitive Obsession

```typescript
/*si se tiene una variable declarada para un valor constante este valor puede estar ocupando espacio
de memoria y generar que el código sea un poco mas pesado debido a esta declaración*/
function verificar(input : number[]) {
  let target = 32 /*Noncompliant*/
  for (let i of input) {
    if (i == target) {
      return true
    }
  }
  return false
}
```
```typescript
/*una forma de solucionar este problema es cambiar el tipo de declaración a una declaración que sea
mas acorde a las especificaciones de la declaración o mas acorde a las necesidades*/
/*aplicando refactoring : rename*/
function verificar(input : number[]) {
  const target = 32
  for (let i of input) {
    if (i == target) {
      return true
    }
  }
  return false
}
```

## Rúbrica

| Criterio                           | Descripción                                                                                                                                                                    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Alcance (4 puntos)                 | El documento resume todos los puntos tratados en la charla.                                                                                                                    |
| Pensamiento Crítico (4 puntos)     | El alumno logra tener una opinión crítica ya sea a favor o en contra de los puntos tratados en la charla, además de sustentarlas correctamente con razones técnicas valederas. |
| Redacción y ortografía  (2 puntos) | El documento se encuentra redacto de una manera que se entiende fácilmente y no cuenta con faltas ortográficas                                                                 |
| Implementación (8 puntos) 	     | Implementa correctamente los code smells así como su corrección (2 puntos por cada code smell y sus técnicas de refactoring)                                                   |
| Sustento (2 puntos)                | El alumno sustenta correctamente la aplicación de ciertas técnicas de refactoring (0.5 por cada code smell).                                                                   |

## Referencias

- https://www.markdowntutorial.com/
- https://code.visualstudio.com/docs/languages/markdown
- Fowler, M. (2019). Refactoring: Improving the design of existing code. Boston: Addison-Wesley.
