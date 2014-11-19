# Hello World 

Não é necessário uma função main ou um include de stantard library, por exemplo. Tão simples como:

```swift
println("Hello World")
```

# Constantes e Variáveis

Se o valor não vai ser mutável priorizamos o uso de constantes (com let):

```swift
let languageName: String = "Swift"
//languageName = "Java" // não compila

let introduced: Int = 2014
let isAwesome: Bool = true
```
Vantagem: otimização e legibilidade. 

Se queremos um valor mutável temos como utilizar a keyword *var*:

```swift
var version: Double = 1.0
version = 1.1 // compila normalmente
```

Inferência de tipos:

```swift
let aString = "Swift"  // O compilador infere que é String
let aDouble = 2014     // O compilador infere que é Double
let aBool = true       // O compilador infere que é Bool
var anInt = 1.0        // O compilador infere que é Int
```

Suporte a unicode:

```swift
let π = 3.1415 // pi
```