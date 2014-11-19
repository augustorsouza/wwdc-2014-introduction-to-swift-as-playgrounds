# Extensions

Pode-se extender o comportamento de qualquer classe, enum ou struct em swift:

```swift
struct Size {
    var width, height: Double
}

extension Size {
    mutating func increaseByFactor(factor: Double) {
        width *= factor
        height *= factor
    }
}

extension Int {
    func repetitions(task: () -> ()) {
        for i in 0..<self {
            task()
        }
    }
}
```

Usando a extension de Int (da standard library!):

```swift
// com parenteses

5.repetitions({
    println("Hello!")
})

// sem parenteses

5.repetitions {
    println("Hello!")
}
```

# Generics

Para generalizar um comportamento de maneira a funcionar com diferentes tipos de objetos podemos utilizar Generics. Exemplo:

```swift
// sem uso de generics, nossa pilha só funciona com Int
class IntStack {
    var elements = [Int]()
    
    func push(element: Int) {
        elements.append(element)
    }
    
    func pop() -> Int {
        return elements.removeLast()
    }
}

// com uso de generics, evita duplicidade e funciona com qualquer tipo
class Stack<T> {
    var elements = [T]()
    
    func push(element: T) {
        elements.append(element)
    }
    
    func pop() -> T {
        return elements.removeLast()
    }
}

let doubleStack = Stack<Double>()
doubleStack.push(10.0)
let lastDouble = doubleStack.pop()

let stringStack = Stack<String>()
stringStack.push("Hello")
println("stringStack elem: \(stringStack.pop())")
```