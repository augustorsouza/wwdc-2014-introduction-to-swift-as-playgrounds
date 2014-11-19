# Classes

Classes são definidas assim: 

```swift
import Foundation

class Vehicle {
    // iVars e properties são a mesma coisa em Swift
    var numberOfWheels = 0 
    
    // Computed property example:
    var description: String {
        get {
            return "\(numberOfWheels) wheels"
        }
        // set {} poderia ser posto aqui
    }
}

let someVehicle = Vehicle() // tipo inferido: Vehicle
println(someVehicle.description)

someVehicle.numberOfWheels = 2 
println(someVehicle.description)
```

Initiliazer e herança:

```swift
class Bycicle: Vehicle {
    // initiliazers não retornam valor, garante que todos os "stored values" foram setados 
    override init() {
        super.init() // chance da super classe se inicializar
        numberOfWheels = 2
    }
}

class Car: Vehicle {
    var speed = 0.0
    override init() {
        super.init() 
        numberOfWheels = 4
    }
    
    // Override de properties
    override var description: String {
        // Como só temos o getter podemos omitir por enquanto as keywords get e set
        return super.description + ", \(speed) km/h"
    }
}

let myCar = Car()
println(myCar.description)

myCar.speed = 35.0
println(myCar.description)
```

Observando mudanças nas properties:

```swift
// Exemplo de property observers 

class ParentsCar: Car {
    override var speed: Double {

        willSet {
            // newValue pode ser utilizado aqui
            if newValue > 80.0 {
                println("Careful now.")
            }
        }

        didSet {
            // oldValue pode ser utilizado aqui
        }
    }
}
```

Adicionando métodos a nossas classes

```swift
class Counter {
    var count = 0
    
    // Exemplo sem parametro
    func increment() {
        count++
    }
    
    // Exemplo com parametro
    func incrementBy(amount: Int) {
        count += amount
    }
    
    // Exemplo com self obrigatório
    func resetToCount(count: Int) {
        self.count = count
    }
}
```