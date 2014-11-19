# Strings

Poderoso como NSString e totalmente compatível: 

```swift
import Foundation

let components = "~/Documents/Swift".pathComponents
let capitalized = "i appear to be a string".capitalizedString
```

Toda String em Swift é uma coleção de caracteres:

```swift
for character in "mouse" {
    println(character)
}

for character in "mús" {
    println(character)
}

for character in "⿏鼠标" { 
    println(character)
}

for character in "🐭🐭🐭🐭🐭" {
    println(character)
}
```

Para criar um caracter a tipagem deve ser explicita

```swift
let dog: Character = "🐶"
```

Pode-se combinar esses caracteres a outros caracteres ou a strings:

```swift
let cow: Character = "🐮"
let dogCow = "\(dog)\(cow)"
let instruction = "Beware of the \(dog)"
```

Interpolação:

```swift
let a = 3, b = 5
//let a = 10, b = 2
let mathResult = "\(a) times \(b) is \(a * b)"
```

Mutabilidade:

```swift
var variableString = "Horse"
variableString += " and carriage"
```