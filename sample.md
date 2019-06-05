# Asignación 2 - Ingeniería de Software 2

## Integrantes

- Guillermo Baca **20151635**
- Miguel Colina **20150346**
- Pelmef Méndez **20150865**
- Javier Ramírez **20152241**
- Caleb Santiago **20152339**

## Resúmen de Charla por Martin Fowler

Aquí va el resúmen.

## Conclusiones

Aquí van las conclusiones.  
¿Qué considera que son los puntos más importantes que se mencionan en la presentación? ¿Por qué lo considera?

## Ejemplos de Code Smells

### Ejemplo 1: Data Clumps

```typescript
class User {
    ...
    /*los siguientes métodos toman una lista de parámetros muy similares por lo que se       
    deberán agrupar en una clase independiente, debido a que al tener una larga lista de 
    parámetros podría conllevar a fallas del código, conflictos y difíciles pruebas de unidad*/
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
    /*se utiliza la técnica de refactoring 'dividir código en piezas lógicas (extract class)' 
    al crear otra clase que agrupa a la lista de parámetros como atributos propios y utiliza 
    métodos reservados de tipo 'get' para devolver dichos elementos a través de su instancia 
    como objeto*/
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
/*Se posee una clase que puede tener gran cantidad de atributos sin embargo se implementa un método el cual busca imprimir la factura, para lo cual llama al método imprimir encabezado y en el mismo método imprime otros atributos lo cual en múltiples llamadas puede generar un desorden al tener un método que llama a otro metodo ademas de hacer la llamada a otros atributos.*/
class Factura{
   nombre:String="";
   cantidad:number=0;
   ruc: number=0;
   monto:number=0;
   codigo:number=0;
   conIGV:boolean=True;

//...
   constructor(nombre:String,cantidad:number,ruc:number,monto:number
      ,codigo:number,conIGV:boolean){
       this.nombre=nombre;
       this.cantidad=cantidad;
               this.ruc=ruc;
               this.monto=monto;
               this.codigo=codigo;
               this.conIGV=conIGV;
}
   //Antes de la implementación de la técnica de refactoring
   ImprimirFactura():void{
       imprimirEncabezado();
       //Imprime los detalles correspondientes
       console.log(`El nombre del cliente es: ${this.nombre}`)
       console.log(`La cantidad es: ${this.cantidad}`)
       console.log(`El ruc es: ${this.ruc}`)
       console.log(`El monto es: ${this.monto}`)
       console.log(`El código es: ${this.codigo}`)
       console.log(`Es afecta de IGV: ${this.conIGV}`)
   }
   }
}
/* Con la implementación del extract method nos permite tener un código mucho más comprensible y ordenado de manera que podamos ubicar más fácilmente las llamadas y los atributos que buscamos llamar*/ 

   //Después de implementar la técnica de refactoring
   ImprimirFactura():void{
       ImprimirEncabezado();
       ImprimirDetalles();
   }
   ImprimirDetalles():void{
       console.log(`El nombre es: ${this.nombre}`)
       console.log(`La cantidad es: ${this.cantidad}`)
       console.log(`El ruc es: ${this.ruc}`)
       console.log(`El monto es: ${this.monto}`)
       console.log(`El código es: ${this.codigo}`)
       console.log(`Es afecta de IGV: ${this.conIGV}`)

```

### Ejemplo 3: 

```typescript
/*Aquí va el ejemplo 3*/
```

### Ejemplo 4: Duplicate Code

```typescript
/*Si se tiene dos cases en una sentencia switch o dos ramas de if con una implementación similar, son ejemplos de duplicate code*/
switch (i) {
  case 1:
    doFirstThing();
    doSomething();
    break;
  case 2:
    doSomethingDifferent();
    break;
  case 3:  // Noncompliant; duplicates case 1's implementation
    doFirstThing();
    doSomething();
    break;
  default:
    doTheRest();
}

if (a >= 0 && a < 10) {
  doFirstThing();
  doTheThing();
}
else if (a >= 10 && a < 20) {
  doTheOtherThing();
}
else if (a >= 20 && a < 50) {
  doFirstThing();
  doTheThing();  // Noncompliant; duplicates first condition
}
else {
  doTheRest();
}
/* La mejor solución es la combinación de las condicionales y/o cases, para el siguiente ejemplo se puede lograr de dos maneras*/
switch (i) {
  case 1:
    doFirstThing();
    doSomething();
    break;
  case 2:
    doSomethingDifferent();
    break;
  case 3:
    doFirstThing();
    doThirdThing();
    break;
  default:
    doTheRest();
}

if (a >= 0 && a < 10) {
  doFirstThing();
  doTheThing();
}
else if (a >= 10 && a < 20) {
  doTheOtherThing();
}
else if (a >= 20 && a < 50) {
  doFirstThing();
  doTheThirdThing();
}
else {
  doTheRest();
}
/*o*/
switch (i) {
  case 1:
  case 3:
    doFirstThing();
    doSomething();
    break;
  case 2:
    doSomethingDifferent();
    break;
  default:
    doTheRest();
}

if ((a >= 0 && a < 10) || (a >= 20 && a < 50)) {
  doFirstThing();
  doTheThing();
}
else if (a >= 10 && a < 20) {
  doTheOtherThing();
}
else {
  doTheRest();
}

```

### Ejemplo 5: 

```typescript
/*Si se tiene una variable declarada para un valor constante este valor puede estar ocupando espacio de memoria y generar que el código sea un poco mas pesado debido a esta declaración*/
//Codigo smells
 function verificar(input: number[]) {
   let target = 32;  // Noncompliant
   for (let i of input) {
     if (i == target) {
       return true;
     }
   }
   return false;
 }
/*una forma de solucionar este problema es cambiar el tipo de declaración a una declaración que sea mas acorde a las especificaciones de la declaración o mas acorde a las necesidades*/
//Aplicando refactoring : rename 
function verificar(input: number[]) {
   const target = 32;
   for (let i of input) {
      if (i == target) {
       return true;
     }
   }
   return false;
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
