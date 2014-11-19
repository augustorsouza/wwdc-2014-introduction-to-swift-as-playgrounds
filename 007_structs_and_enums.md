# Structures

Alguns exemplos:

```swift
import Foundation
import UIKit

struct Point {
    var x, y: Double
}

struct Size {
    var width, height: Double
}

struct Rect {
    var origin: Point
    var size: Size
    
    // Computed properties
    var area: Double {
        return size.width * size.height
    }
    
    // Methods
    func isBiggerThanRect(other: Rect) -> Bool {
        return self.area > other.area
    }
}

// Initiliazers default, mas é possível oferecer outras versões também 
var point = Point(x: 0.0, y: 0.0)
var size = Size(width: 640.0, height: 480.0)
var rect = Rect(origin: point, size: size)
```

Diferenças entre structs e classes: Structs são passadas por valor enquanto instâncias de classes são passadas por referência e não existe herança com Structs.

Para permitir que properties em structs mudem, deve-se utilizar a keyword *mutating*

```swift
struct AnotherPoint {
    var x, y: Double
    
    mutating func moveToTheRightBy(dx: Double) {
        x += dx
    }
}

var point1 = AnotherPoint(x: 0.0, y: 0.0)
point1.x = 1.0
point1.y = 1.0

let point2 = AnotherPoint(x: 0.0, y: 0.0)
// point2.x = 1.0 // Não é permitido
```

# Enumerations

Podem ser com valores "raw" como em C:

```swift
enum Planet: Int {
    case Mercury = 1, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
}

let earthNumber = Planet.Earth.rawValue // = 3
```

Pode-se também utilizar outros objetos como valores no enum:

```swift
enum ControlCharacter: Character {
    case Tab = "\t"
    case Linefeed = "\n"
    case CarriageReturn = "\r"
}
```

Pode-se também se utilizar um valor que você definiu (não baseado em nenhum tipo pré-definido)

```swift
enum CompassPoint {
    case North, South, East, West
}

var directionToHead = CompassPoint.West // inferencia: CompassPoint
directionToHead = .East // como o compilador sabe o tipo, é simples assim para se reatribuir o valor

// Exemplo com label
let label = UILabel()
label.textAlignment = .Right // legível e conciso
```

Enums com valores associados:

```swift
enum TrainStatus {
    case OnTime
    case Delayed(Int) // atrasado por alguns minutos
    
    init() {
        self = OnTime
    }
    
    var description: String {
        switch self {
            case OnTime:
                return "On time"
            case Delayed(let minutes):
                return "Delayed by \(minutes) minute(s)"
        }
    }
}

var status = TrainStatus() 
println("The train is \(status.description)")

status = .Delayed(42)
println("The train is now \(status.description)")
```

Utilizando em uma classe:

```swift
class Train {
    enum Status {
        case OnTime, Delayed(Int)

        init() {
            self = OnTime
        }

        var description: String {
            switch self {
                case OnTime:
                    return "On time"
                case Delayed(let minutes):
                    return "Delayed by \(minutes) minute(s)"
            }
        }
    }
    
    var status = Status()
}

let train = Train()
println("The train is now \(train.status.description)")
```
