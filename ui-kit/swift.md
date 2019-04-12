## UIKit - swift

### Strings

```
let greeting = "Hello"
```

#### Multiline 

```
let joke = """
  Q: Why did the chicken cross the road?
  A: To get to the other side!
  """
```

#### Escaping strings

```
let greeting = "It is traditional in programming to print
\"Hello, world!\""
```

#### Check if string is empty

```
var myString = ""
 
if myString.isEmpty {
  print("The string is empty")
}
```

#### Character type

```
let a = "a" //'a' is a String
let b: Character = "b" //'b' is a Character
```

#### Concatenation

```
let string1 = "Hello"
let string2 = ", world!"
let myString = string1 + string2 // "Hello, world!
```

```
var myString = "Hello"
myString = myString + ", world!" // "Hello, world!"
myString += " Hello!" // "Hello, world! Hello!
```

#### Interpolation

```
let name = "Rick"
let age = 30
print("\(name) is \(age) years old") //Rick is 30 years old
```

### Functions

```
function functionName (parameters) -> ReturnType {
  //body of the function 
}
```

#### Parameters

All function parameters are typed.

```
func triple(value: Int) {
  let result = value * 3
  print("If you multiply \(value) by 3, you'll get \(result).")
}
```

When calling a function, it's arguments are named.

```
triple(value: 10)
```

Parameters inside a function can be labelled differently to how they are added as arguments

```
func sayHello(to person: String, and anotherPerson: String) {
  print("Hello \(person) and \(anotherPerson)")
}
```

```
sayHello(to: "Phill", and: "Laura")
```

When defining a function, you can choose to omit the parameter labels:

```
func sayHello(_ person: String, _ anotherPerson: String) {
  print("Hello \(person) and \(anotherPerson)")
}
```

```
sayHello("Phill", "Laura")
```

#### Default parameter values

Function parameters can have default values if nothing is passed in as an argument. In this case, the parameter must always be labelled.

```
func sayHello(to person: String = "Phill",and _ anotherPerson: String = "Laura") {
  print("Hello \(person) and \(anotherPerson)")
}
```

```
sayHello()
```

#### Returning values

You always need to specify a return type when returning a value from a function.

```
func multiply(firstNumber: Int, secondNumber: Int) -> Int {
  let result = firstNumber * secondNumber
  return result
}
```

### Structures

Structs are a way to define your own custom types (think of structs as classes in JavaScript).

```
struct Person {
  var name: String
  func sayHello() {
    print("Hello, there! My name is \(name)!")
  }
}
```

An instance of this type can be created, passing in values for the memberwise initilizers. These are the initilizers for the instance properties.

```
let person = Person(name: "Jasmine")
person.sayHello()
```

#### Initilizers

You can initilize a variable with a default value by calling an initilizer on a type

```
var string = String() // ""
var integer = Int() // 0
var bool = Bool() // false
```

If you want to perform custom logic when an instance property is being initialized a custom initializer can be added to a struct to define the instance properties

```
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

```
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

#### Default values

When initializing structs, all instance properties must be set. Default values can be used inside a struct to do this.

```
struct Odometer {
  var count: Int = 0
}
```

#### Instance methods

Instance methods are functions that can be called on specific instances of a type. They provide ways to access and modify properties of the structure, and they add functionality that relates to the instance's purpose.

```
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

#### Mutating methods

If you want to update an instance property from within a structs instance method, a mutating method must be used.

```
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

```
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

```
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

```
struct Temperature {
  static var boilingPoint = 100
}
```

### Value type

Structs are passed by value, as opposed to being passed by reference. This mean that when they are assigned to new variables or passed into functions, a copy of the struct is made and any changes to it won't be reflected in the original.

### Shadowing

In a struct, it is unnecessary to use self when referring to an instance property or method of the struct. Although you can, shadowing means the compiler will understand that you are referring to a property owned by the struct. The only case where this is not true is inside an initializer, when parameters match the property names.

