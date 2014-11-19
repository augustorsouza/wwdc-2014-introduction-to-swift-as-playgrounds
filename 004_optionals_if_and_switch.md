# Optionals

Utilizados quando pode-se ter um valor ou não (nil):

```swift
import Foundation

let numberOfLegs = ["ant": 6, "snake": 0, "cheetah": 4]
let possibleLegCount = numberOfLegs["aardvark"] // Tipo: Int?
```

Operador para unwrap (!) e sintaxe especial:

```swift
if possibleLegCount == nil {
    println("Aardvark wasn't found")
} else {
    let legCount = possibleLegCount! // Tipo: Int
    println("An aardvark has \(legCount) legs")
}

// Ou...

if possibleLegCount != nil {
    let legCount = possibleLegCount!
    println("An aardvark has \(legCount) legs")
}

// Ou... (sintaxe especial e mais comum)

if let legCount = possibleLegCount {
    println("An aardvark has \(legCount) legs")
}
```

# If

Parenteses são opcionais mas chaves são requeridas

```swift
if (possibleLegCount == 0) {
    println("It slithers and slides arround")
} else {
    println("It walks")
}

// Ou...

if possibleLegCount == 0 {
    println("It slithers and slides arround")
} else {
    println("It walks")
}
```

# Switch

Para substituir uma cadeia de ifs se usa um switch. O comando não precisa de break, mas precisa obrigatoriamente de uma saída "default":

```swift
if possibleLegCount == 0 {
    println("It slithers and slides arround")
} else if possibleLegCount == 1 {
    println("It hops")
} else {
    println("It walks")
}

// Melhor:
var legCount = 0

switch legCount {
    case 0: 
        println("It slithers and slides arround")
    case 1:
        println("It hops")
    default:
        println("It walks")
}
```

Pode-se fazer match com qualquer tipo de objeto, não só com inteiros:

```swift
let aString = "Uma string"

switch aString {
    case "Uma string": 
        println("Entrou no primeiro case")
    case "Outra string":
        println("Entrou no segundo case")
    default:
        println("Entrou no default case")
}
```

Switches são poderosos:

```swift
// Match com múltiplos valores
legCount = 3
switch legCount {
    case 0: 
        println("It slithers and slides arround")
    case 1, 3, 4, 7, 9, 11, 13:
        println("It limps")
    default:
        println("It walks")
}

// Match com range
switch legCount {
    case 0: 
        println("It has no legs")
    case 1...8:
        println("It has a few legs")
    default:
        println("It has lots of legs")
}
```