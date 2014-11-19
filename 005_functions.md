# Functions

Funções são "first-class citizens" em swift:

```swift
import Foundation

// Função sem parametros
func sayHello1() {
    println("Hello")
}
sayHello1()

// Função com multiplos parametros nomeados
func sayHello2(to name1: String, from name2: String) {
    println("Hello \(name1) -- \(name2)")
}
// ou...
//func sayHello2(#to: String, #from: String) {
//    println("Hello \(to) -- \(from)")
//}

sayHello2(to: "World", from: "sayHello2")

// Função com valor default
func sayHello3(to: String = "World", from: String = "sayHello3") {
    println("Hello \(to) -- \(from)")
}
sayHello3(to: "World!!!!!", from: "Augusto")
sayHello3()
```

Retornos:

```swift
func buildGreeting(name: String = "World") -> String {
    return "Hello " + name
}

let greeting = buildGreeting() // Tipo String (inferencia)
```

Multiplos retornos (tuples)

```swift
func refreshWebPage() -> (Int, String) {
    return (200, "Success")
}

let (statusCode, message) = refreshWebPage() // inferencia: statudeCode é Int e message é String
println("Received \(statusCode): \(message)")
```

Outro uso de tuplas:

```swift
var numberOfLegs = ["ant": 6, "snake": 0, "cheetah": 4]
for (animalName, legCount) in numberOfLegs {
    println("\(animalName)s have \(legCount) legs")
}
```

Tuplas nomeadas:

```swift
func refreshWebPage2() -> (code: Int, message: String) {
    return (200, "Success")
}
let status = refreshWebPage2()
println("Received \(status.code): \(status.message)")
```

Closures (em swift funções são closures nomeadas):

```swift
let greetingPrinter = {
    println("Hello World")
}
greetingPrinter()

// Passando closures por parametro:
func repeat(times: Int, task: () -> ()) {
    for i in 0..<times {
        task()
    }
}

// Chamando: forma 1
repeat(2, {
    println("Hello World")
})

// Chamando: forma 2
repeat(2) {
    println("Hello World")
}
```
