# UIKit - swift

## Strings

```swift
let greeting = "Hello"
```

### Multiline 

```swift
let joke = """
  Q: Why did the chicken cross the road?
  A: To get to the other side!
  """
```

### Escaping strings

```swift
let greeting = "It is traditional in programming to print
\"Hello, world!\""
```

### Check if string is empty

```swift
var myString = ""
 
if myString.isEmpty {
  print("The string is empty")
}
```

### Character type

```swift
let a = "a" //'a' is a String
let b: Character = "b" //'b' is a Character
```

### Concatenation

```swift
let string1 = "Hello"
let string2 = ", world!"
let myString = string1 + string2 // "Hello, world!
```

```swift
var myString = "Hello"
myString = myString + ", world!" // "Hello, world!"
myString += " Hello!" // "Hello, world! Hello!
```

### Interpolation

```swift
let name = "Rick"
let age = 30
print("\(name) is \(age) years old") //Rick is 30 years old
```

## Functions

```swift
function functionName (parameters) -> ReturnType {
  //body of the function 
}
```

### Parameters

All function parameters are typed.

```swift
func triple(value: Int) {
  let result = value * 3
  print("If you multiply \(value) by 3, you'll get \(result).")
}
```

When calling a function, it's arguments are named.

```swift
triple(value: 10)
```

Parameters inside a function can be labelled differently to how they are added as arguments

```swift
func sayHello(to person: String, and anotherPerson: String) {
  print("Hello \(person) and \(anotherPerson)")
}
```

```swift
sayHello(to: "Phill", and: "Laura")
```

When defining a function, you can choose to omit the parameter labels:

```swift
func sayHello(_ person: String, _ anotherPerson: String) {
  print("Hello \(person) and \(anotherPerson)")
}
```

```swift
sayHello("Phill", "Laura")
```

### Default parameter values

Function parameters can have default values if nothing is passed in as an argument. In this case, the parameter must always be labelled.

```swift
func sayHello(to person: String = "Phill",and _ anotherPerson: String = "Laura") {
  print("Hello \(person) and \(anotherPerson)")
}
```

```swift
sayHello()
```

### Returning values

You always need to specify a return type when returning a value from a function.

```swift
func multiply(firstNumber: Int, secondNumber: Int) -> Int {
  let result = firstNumber * secondNumber
  return result
}
```

## Structures

Structs are a way to define your own custom types (think of structs as classes in JavaScript).

```swift
struct Person {
  var name: String
  func sayHello() {
    print("Hello, there! My name is \(name)!")
  }
}
```

An instance of this type can be created, passing in values for the memberwise initilizers. These are the initilizers for the instance properties.

```swift
let person = Person(name: "Jasmine")
person.sayHello()
```

### Initilizers

You can initilize a variable with a default value by calling an initilizer on a type

```swift
var string = String() // ""
var integer = Int() // 0
var bool = Bool() // false
var myArray = [Int]() // []
var myArray = [Int](repeating: 0, count: 100)
var myDictionary = [String: Int]() // [:]
```

If you want to perform custom logic when an instance property is being initialized a custom initializer can be added to a struct to define the instance properties

```swift
struct Person {
    var firstName: String
    var lastName: String
    var age: Int
    
    init(firstName: String, lastName: String, age: Int) {
        self.firstName = firstName
        self.lastName = lastName
        self.age = age
    }

    func sayHello() {
        print("Hi, my name is \(self.firstName) \(self.lastName) and I am \(age) years old")
    }
}
```

You can also add multiple custom initializers to represent different ways in which the struct may be created.

```swift
struct Person {
    var firstName: String
    var lastName: String
    var age: Int
    
    init(firstName: String, lastName: String, age: Int) {
        self.firstName = firstName
        self.lastName = lastName
        self.age = age
    }

    func sayHello() {
        print("Hi, my name is \(self.firstName) \(self.lastName) and I am \(age) years old")
    }
}

``` 

### Default values

When initializing structs, all instance properties must be set. Default values can be used inside a struct to do this.

```swift
struct Odometer {
  var count: Int = 0
}
```

### Instance methods

Instance methods are functions that can be called on specific instances of a type. They provide ways to access and modify properties of the structure, and they add functionality that relates to the instance's purpose.

```swift
struct Size {
  var width: Double
  var height: Double
 
  func area() -> Double {
    return width * height
  }
}
 
let someSize = Size(width: 10.0, height: 5.5)
let area = someSize.area() // Area is assigned a value of 55.0
```

### Mutating methods

If you want to update an instance property from within a structs instance method, a mutating method must be used.

```swift
struct Odometer {
  var count: Int = 0 // Assigns a default value to the `count` 
  property. 
 
  mutating func increment() {
    count += 1
  }
 
  mutating func increment(by amount: Int) {
    count += amount
  }
 
  mutating func reset() {
    count = 0
  }
}
```

### Computed properties

Swift has a feature that allows a property to perform logic that returns a calculated value.

```swift
struct Temperature {
  var celsius: Double
 
  var fahrenheit: Double {
    return celsius * 1.8 + 32
  }
 
  var kelvin: Double {
    return celsius + 273.15
  }
}
```

### Property observers

Swift allows you to observe any property and respond to the changes in the property's value. These property observers are called every time a property's value is set, even if the new value is the same as the property's current value.

```swift
struct StepCounter {
    var totalSteps: Int = 0 {
        willSet {
            print("About to set totalSteps to \(newValue)")
        }
        didSet {
            if totalSteps > oldValue  {
                print("Added \(totalSteps - oldValue) steps")
            }
        }
    }
}
```

### Type properties and methods

Swift also supports adding type properties and methods, which can be accessed or called on the type itself. Use the static keyword to add a property or method to a type.
Type properties are useful when a property is related to the type, but not a characteristic of an instance itself.

These are the same as static properties and methods in JavaScript.

```swift
struct Temperature {
  static var boilingPoint = 100
}
```

### Value type

Structs are passed by value, as opposed to being passed by reference. This mean that when they are assigned to new variables or passed into functions, a copy of the struct is made and any changes to it won't be reflected in the original.

### Shadowing

In a struct, it is unnecessary to use self when referring to an instance property or method of the struct. Although you can, shadowing means the compiler will understand that you are referring to a property owned by the struct. The only case where this is not true is inside an initializer, when parameters match the property names.

## Classes

Classes are very similar to structs. The difference is that classes are passed by reference and also have some additional features like inheritance. It is recommended to try and use structs over classes to avoid the pitfalls of brittle classes and subclasses. If you want to subclass structs, a protocol pattern can be used as opposed to inheritance.

```swift
class Person {
  let name: String
 
  init(name: String) {
    self.name = name
  }
 
  func sayHello() {
    print("Hello, there!")
  }
 }
```

Classes are defined in the say way as structs except replacing struct -> class. Also notice that there is no auto initializer for instance properties. Classes must have an init.

### Subclassing

```swift
class SomeSubclass: SomeSuperclass {
    // subclass definition goes here
}
```

### Overriding superclass methods

```swift
class Train: Vehicle {
    override func makeNoise() {
        print("Choo Choo!")
    }
}
```

### Overriding superclass instance properties

```swift
class Car: Vehicle {
    var gear = 1
    override var description: String {
        return super.description + " in gear \(gear)"
    }
}
```

### Overriding superclass initializer

```swift
class Student: Person {
  var favoriteSubject: String
 
  init(name: String, favoriteSubject: String) {
    self.favoriteSubject = favoriteSubject
    super.init(name: name)
  }
}
```

## Arrays

```swift
var numbers = [1, -3, 50, 72, -95, 115]
```

```swift
let numbers: [Int8] = [1, -3, 50, 72, -95, 115]
```

```swift
var myArray: Array<Int> = []
```

Unlike JavasScript, once you define an array a constant, you can't modify its internal values.

### Accessing array

```swift
let firstName = names[0]
```

### Update array 

```swift
names[1] = "Paul"
```

### Append to array

```swift
names.append("Joe")
```

```swift
names += ["Keith", "Jane"]
```

### Insert in array

```swift
names.insert("Bob", at: 0)
```

### Remove from array

```swift
var names = ["Amy", "Brad", "Chelsea", "Dan"]
let chelsea = names.remove(at:2)
let dan = names.removeLast()
names.removeAll()
```

### Concatenating arrays

```swift
var myNewArray = firstArray + secondArray
```

## Dictionaries

Same as JavaScript Sets.

```swift
[key1 : value1, key2: value2, key3: value3]
```

### Adding to a set

```swift
scores["Oli"] = 399
```

### Checking if a value exists before updating

```swift
let oldValue = scores.updateValue(100, forKey: "Richard") // will return nil if no value, the old value if there is one. But the value is still updated/added even if nil is returned
```

Swift uses if-let syntax to let you run code only if a value is returned from the method. If there wasn't an existing value, the code within the brackets won't be executed.

```swift
if let oldValue = scores.updateValue(100, forKey: "Richard") {
  print("Richard's old value was \(oldValue)")
}
```

### Removing an item from a set

```swift
var scores = ["Richard": 100, "Luke": 400, "Cheryl": 800]
scores["Richard"] = nil //["Luke": 400, "Cheryl": 800]
```

If you need access to the old value before removing it.

```swift
if let oldValue = scores.removeValue(forKey: "Luke") {
  print("Luke's score was \(oldValue) before he stopped 
  playing")
}
```

### Getting all keys or all values of a dictionary

```swift
var scores = ["Richard": 500, "Luke": 400, "Cheryl": 800]
 
let players = Array(scores.keys) //["Richard", "Luke", "Cheryl"]
let points = Array(scores.values) //[500, 400, 800]
```

### Looking up a key in a dictionary

```swift
// If there's no key, code within the brackets won't run
if let myScore = scores["Luke"] {
  print(myScore)
}
```

## Loops

### For in loop

```swift
for index in 1...5 {
  print("This is number \(index)")
}
```

```swift
let names = ["Joseph", "Cathy", "Winston"]
for name in names {
  print("Hello \(name)")
}
```

```swift
for (index, letter) in "ABCD".characters.enumerated() {
  print("\(index): \(letter)")
}
```

```swift
let vehicles = ["unicycle" : 1, "bicycle" : 2, "tricycle" : 3, 
"quad bike" : 4] 
for (vehicleName, wheelCount) in vehicles {
  print("A \(vehicleName) has \(wheelCount) wheels")
}
```

#### Breaking out of For in loop

```swift
for counter in -3...3 {
  print(counter)
  if counter == 0 {
    break
  }
}
```