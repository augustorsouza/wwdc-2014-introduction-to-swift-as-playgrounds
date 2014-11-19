# Arrays e Dictionaries

Poderosos como NSArray e NSDictionary e totalmente compatíveis: 

```swift
import Foundation

let components = "~/Documents/Swift".pathComponents // retorna um Array de swift não um NSArray
```

Arrays e dicionários podem armazenar qualquer tipo, não é necesssário que sejam objetos (como era em Objective-C):

```swift
var names = ["Anna", "Alex", "Brian", "Jack"]
var numberOfLegs = ["ant": 6, "snake": 0, "cheetah": 4]
```

Principal diferença com Objective-c: *as coleções são tipadas*

```swift
names.append("Augusto")
// names.append(1) // não funciona

numberOfLegs["spider"] = 8
// numberOfLegs["spider"] = "oito" // não funciona
```

# Loops

Existem: while, do-while, for e for-in

```swift
var i = 0 // contador auxiliar

while i < 2 {
    println("Olá")
    i++
}

i = 0

do {
    println("Olá")
    i++
} while i < 2

for i = 0; i < 2; i++ {
    println("Olá")
}

for character in "🐭🐭🐭🐭🐭" {
    println(character)
}
```

For-in é muito poderoso, outros exemplos:

```swift
// Ranges
for number in 1...5  {
    println("\(number) times 4 is \(number * 4)")
}

for number in 1..<5  {
    println("\(number) times 4 is \(number * 4)")
}

// Array

for name in names {
    println(name)
}

for name in ["Anna", "Alex", "Brian"] {
    println(name)
}

// Dictionaries

for (animalName, legCount) in numberOfLegs {
    println("\(animalName)s have \(legCount) legs")
}
// (animalName, legCount) é uma tupla
```

Modificando arrays e dictionaries:

```swift
// Arrays

var shoppingList = ["Eggs", "Milk"]
shoppingList.append("Flour")                    // primeira forma
shoppingList.append("Cheese")                   // segunda forma
shoppingList += ["Butter", "Chocolate Spread"]  // terceira forma

shoppingList[0] = "Six eggs"                    // modificando um unico elemento
shoppingList[3...4] = ["Bananas", "Apples"]     // modificando múltiplos elementos

// Dictionaries
var shoppingListWithQuantities = ["eggs": 6, "milk": 2, "butter": 1]
shoppingListWithQuantities["chocolate"] = 1
```