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
    /*los siguientes métodos toman una lista de parámetros muy similares por lo que se deberán agrupar en una clase independiente, debido a que al tener una larga lista de parámetros podría conllevar a fallas del código, conflictos y difíciles pruebas de unidad*/
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
    /*se utiliza la técnica de refactoring 'dividir código en piezas lógicas (extract class)' al crear otra clase que agrupa a la lista de parámetros como atributos propios y utiliza métodos reservados de tipo 'get' para devolver dichos elementos a través de su instancia como objeto*/
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

/*luego de implementar la técnica de refactoring*/
class User {
    ...
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

Aquí va el ejemplo 2. 

### Ejemplo 3: 

Aquí va el ejemplo 3. 

### Ejemplo 4: 

Aquí va el ejemplo 4.

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